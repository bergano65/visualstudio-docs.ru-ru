---
title: Создание системы базового проекта. часть 1 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97fee2a4480f3fe8e5439decfd4852a020a734ff
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232261"
---
# <a name="create-a-basic-project-system-part-1"></a>Создание системы базового проекта, часть 1
В Visual Studio проекты — это контейнеры, используемые разработчиками для организации файлов исходного кода и других ресурсов. Проекты отображаются как дочерние элементы решений в **обозревателе решений**. Проекты позволяют упорядочивать, создание, отладку и развертывать исходный код и создавать ссылки на Web services, баз данных и другие ресурсы.  
  
 Проекты определены в файлах проекта, например *.csproj* файла для проекта Visual C#. Можно создать собственный тип проекта, который имеет собственные расширение имени файла проекта. Дополнительные сведения о типах проектов см. в разделе [типы проектов](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Если необходимо расширить Visual Studio с помощью пользовательского типа проекта, настоятельно рекомендуется использование [система проектов Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSP) которого имеет ряд преимуществ по сравнению с создания проекта системы с нуля:  
>   
>  -  Проще адаптации.  Даже системы базового проекта требует десятки тысяч строк кода.  Используя поставщики службы Виртуализации снижает стоимость адаптации в несколько щелчков мышью, прежде чем вы будете готовы настраивать его под свои нужды.  
>  -  Упрощает обслуживание.  Используя поставщики службы Виртуализации, необходимо только обслуживать собственные сценарии.  Мы занимаемся ведении всю инфраструктуру системы проекта.  
>   
>  Если вам нужно предназначенные для версий старше, чем Visual Studio 2013 Visual Studio, не можно использовать поставщики службы Виртуализации в расширении Visual Studio.  Если это так, в этом пошаговом руководстве хорошо подходит для начала.  
  
 В этом пошаговом руководстве показано, как создать тип проекта, который имеет расширение имени файла проекта *.myproj*. В этом пошаговом руководстве использует существующие системы проекта Visual C#.  
  
> [!NOTE]
>  Дополнительные примеры проектов расширения, см. в разделе [примеры VSSDK](http://aka.ms/vs2015sdksamples).  
  
 В этом пошаговом руководстве объясняется, как выполнять эти задачи:  
  
-   Создание типа базового проекта.  
  
-   Создайте шаблон базовый проект.  
  
-   Зарегистрируйте шаблон проекта в Visual Studio.  
  
-   Создайте экземпляр проекта, открыв **новый проект** диалоговое окно, а затем с помощью шаблона.  
  
-   Создайте фабрику проекта для вашей системы проекта.  
  
-   Создайте узел проекта для вашей системы проекта.  
  
-   Добавление пользовательских значков для системы проектов.  
  
-   Реализуйте замена параметров базового шаблона.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Необходимо также загрузить исходный код для [Managed Package Framework для проектов](http://mpfproj12.codeplex.com/). Извлеките файл в расположении, доступном для решения, которое вы собираетесь создать.  
  
## <a name="create-a-basic-project-type"></a>Создание базового проекта типа  
 Создайте проект VSIX C# с именем **SimpleProject**. (**Файл** > **новый** > **проекта** и затем **Visual C#**  >   **Расширяемость** > **проект VSIX**). Добавление шаблона элемента проекта пакета Visual Studio (на **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить** > **новый элемент**, затем перейдите к разделу **Расширяемости** > **пакет Visual Studio**). Назовите файл *SimpleProjectPackage*.  
  
## <a name="creating-a-basic-project-template"></a>Создание базового проекта шаблона  
 Теперь можно изменить этот базовый VSPackage для реализации нового *.myproj* тип проекта. Чтобы создать проект, основанный на *.myproj* типа проекта, Visual Studio должен знать, какие файлы, ресурсы и ссылки для добавления нового проекта. Чтобы предоставить эти сведения, поместите файлы проекта в папку шаблона проекта. Когда пользователь вводит *.myproj* проекта для создания проекта, файлы копируются в новый проект.  
  
### <a name="to-create-a-basic-project-template"></a>Создание базового проекта шаблона  
  
1.  Добавьте в проект, друг под другом три папки: *Templates\Projects\SimpleProject*. (В **обозревателе решений**, щелкните правой кнопкой мыши **SimpleProject** узел проекта, выберите пункт **добавить**, а затем нажмите кнопку **новую папку**. Назовите папку *шаблоны*. В *шаблоны* папки, добавьте папку с именем *проекты*. В *проекты* папки, добавьте папку с именем *SimpleProject*.)  
  
2.  В *Templates\Projects\SimpleProject* папки, добавить файл точечного рисунка, который используется в качестве значка с именем *SimpleProject.ico*. При нажатии кнопки **добавить**, откроется редактор значков.  
  
3.  Сделайте различение значок. Этот значок будет отображаться в **новый проект** диалоговое окно «» далее в этом пошаговом руководстве.  
  
     ![Значок простого проекта](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  Значок сохраните и закройте редактор значков.  
  
5.  В *Templates\Projects\SimpleProject* папки, добавьте **класс** элемента с именем *Program.cs*.  
  
6.  Замените существующий код приведенным ниже.  
  
    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
  
    namespace $nameSpace$
    {  
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```
  
    > [!IMPORTANT]
    >  Это не конечную форму *Program.cs* код; замена параметров будут обработаны позже. Может появиться ошибки компиляции, но в течение его **BuildAction** — **содержимого**, можно построить и запустить проект как обычно.  
  
1.  Сохраните файл.  
  
2.  Копировать *AssemblyInfo.cs* файла из *свойства* папку *Projects\SimpleProject* папки.  
  
3.  В *Projects\SimpleProject* папку добавить XML-файл с именем *SimpleProject.myproj*.  
  
    > [!NOTE]
    >  Расширение имени файла для всех проектов данного типа *.myproj*. Если вы хотите изменить его, необходимо изменить его везде, где оно встречается в этом пошаговом руководстве.  
  
4.  Замените существующее содержимое следующие строки.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
5.  Сохраните файл.  
  
6.  В **свойства** окне **действие при построении** из *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico* , и *SimpleProject.myproj* для **содержимого**и задайте их **включить в VSIX** свойства **True**.  
  
 Этот шаблон проекта описывает базовый Visual C# проект с отладочной конфигурации и конфигурации выпуска. Проект включает два исходных файла *AssemblyInfo.cs* и *Program.cs*и несколько ссылок на сборки. При создании проекта из шаблона ProjectGuid значение автоматически заменяется новый идентификатор GUID.  
  
 В **обозревателе решений**, развернутом **шаблоны** папки должен выглядеть следующим образом:

```
Templates  
   Projects  
      SimpleProject  
         AssemblyInfo.cs  
         Program.cs  
         SimpleProject.ico  
         SimpleProject.myproj  
```

## <a name="create-a-basic-project-factory"></a>Создание базового проекта фабрики  
 Необходимо указать расположение папки шаблона проекта Visual Studio. Чтобы сделать это, добавьте атрибут к классу VSPackage, реализующий фабрику проектов, таким образом, чтобы расположение шаблона записывается в системный реестр, при построении пакета VSPackage. Начните с создания фабрики базовый проект, который определяется параметром фабрику проекта GUID. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут для подключения фабрики проектов для `SimpleProjectPackage` класса.  
  
### <a name="to-create-a-basic-project-factory"></a>Чтобы создать фабрику базового проекта  
  
1.  Создание глобальных уникальных идентификаторов для фабрики проекта (на **средства** меню, щелкните **создать GUID**), или использовать в следующем примере. Добавьте идентификаторы GUID для `SimpleProjectPackage` класс практически разделу с уже определенным `PackageGuidString`. Идентификаторы GUID должны находиться в виде идентификатора GUID и строковый формат. Итоговый код должен выглядеть следующим образом.  
  
    ```csharp  
        public sealed class SimpleProjectPackage : Package
        {  
            ...
            public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
            public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
    
            public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);  
        }  
    ```  
  
3.  Добавьте в начало класса *SimpleProject* папку с именем *SimpleProjectFactory.cs*.  
  
4.  Добавьте следующие операторы using:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Добавьте атрибут GUID, чтобы `SimpleProjectFactory` класса. Значение атрибута — это новый идентификатор GUID фабрики проектов.  
  
    ```csharp  
    [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Теперь вы можете зарегистрировать шаблон проекта.  
  
### <a name="to-register-the-project-template"></a>Для регистрации шаблона проекта  
  
1.  В *SimpleProjectPackage.cs*, добавьте <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут `SimpleProjectPackage` класса, как показано ниже.  
  
    ```csharp  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectPackage.PackageGuidString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
     Перестроение регистрирует шаблон проекта.  
  
 Параметры `defaultProjectExtension` и `possibleProjectExtensions` присваивается расширение имени файла проекта (*.myproj*). `projectTemplatesDirectory` Параметр имеет значение относительный путь к *шаблоны* папки. Во время сборки этот путь будет преобразуются в полной сборки и добавляется в реестр, чтобы зарегистрировать систему проекта.  
  
## <a name="test-the-template-registration"></a>Проверка регистрации шаблона  
 Шаблон регистрации указывает Visual Studio расположение папки шаблона проекта Visual Studio можно отображать имя шаблона и значок в **новый проект** диалоговое окно.  
  
### <a name="to-test-the-template-registration"></a>Чтобы проверить регистрацию шаблона  
  
1.  Нажмите клавишу **F5** запустить отладку экспериментальный экземпляр Visual Studio.  
  
2.  В экспериментальном экземпляре создайте новый проект типа только что созданный проект. В **новый проект** диалоговом окне вы увидите **SimpleProject** под **установленные шаблоны**.  
  
 Теперь у вас есть фабрику проекта, который регистрируется. Тем не менее он еще не удается создать проект. Пакет проекта и фабрики проектов совместно для создания и инициализации проекта.  
  
## <a name="add-the-managed-package-framework-code"></a>Добавьте код, Managed Package Framework  
 Реализуйте соединение между пакет проекта и фабрики проектов.  
  
-   Импортируйте файлы исходного кода для Managed Package Framework.  
  
    1.  Выгрузить проект SimpleProject (в **обозревателе решений**, выберите узел проекта и в контекстном меню щелкните **выгрузить проект**.) и откройте файл проекта в редакторе XML.  
  
    2.  Добавьте следующие блоки в файл проекта (непосредственно над \<импорта > блоков). Задайте `ProjectBasePath` к расположению *ProjectBase.files* файл в только что загруженном коде Managed Package Framework. Может потребоваться добавить обратную косую черту в путь. Если этого не сделать, проект может не найти исходный код Managed Package Framework.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  Не забывайте обратную косую черту в конце пути.  
  
    3.  Перезагрузите проект.  
  
    4.  Добавьте ссылки на следующие сборки:  
  
        -   `Microsoft.VisualStudio.Designer.Interfaces` (в  *\<VSSDK install > \VisualStudioIntegration\Common\Assemblies\v2.0*)  
  
        -   `WindowsBase`  
  
        -   `Microsoft.Build.Tasks.v4.0`  
  
### <a name="to-initialize-the-project-factory"></a>Для инициализации фабрики проектов  
  
1.  В *SimpleProjectPackage.cs* добавьте следующие `using` инструкции.  
  
    ```csharp  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Производные `SimpleProjectPackage` класса из `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```csharp  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Регистрирует фабрику проекта. Добавьте следующую строку к `SimpleProjectPackage.Initialize` метод, сразу после `base.Initialize`.  
  
    ```csharp  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Реализация абстрактного свойства `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  В *SimpleProjectFactory.cs*, добавьте следующий `using` инструкции после существующего `using` инструкций.  
  
    ```csharp  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Производные `SimpleProjectFactory` класса из `ProjectFactory`.  
  
    ```csharp  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Добавьте следующий метод фиктивный `SimpleProjectFactory` класса. Этот метод реализуется в одном из следующих разделов.  
  
    ```csharp  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Добавьте следующие поля и конструктор для `SimpleProjectFactory` класса. Это `SimpleProjectPackage` ссылку кэшируется в скрытом поле, чтобы его можно использовать при установке сайта поставщика услуг.  
  
    ```csharp  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
## <a name="test-the-project-factory-implementation"></a>Тестирование реализации фабрики проектов  
 Проверка вызывается конструктор для реализации фабрики проектов.  
  
### <a name="to-test-the-project-factory-implementation"></a>Для проверки реализации фабрики проектов  
  
1.  В *SimpleProjectFactory.cs* файл, установите точку останова на следующую строку в `SimpleProjectFactory` конструктор.  
  
    ```csharp  
    this.package = package;  
    ```  
  
2.  Нажмите клавишу **F5** запустить экспериментальный экземпляр Visual Studio.  
  
3.  В экспериментальном экземпляре приступить к созданию нового проекта. В **новый проект** выберите **SimpleProject** тип проекта, а затем нажмите кнопку **ОК**. Выполнение прекратится в точке останова.  
  
4.  Удалите точку останова и остановить отладку. Так как мы еще не создали узел проекта, код создания проекта по-прежнему создает исключения.  
  
## <a name="extend-the-projectnode-class"></a>Расширение класса ProjectNode  
 Теперь вы можете реализовать `SimpleProjectNode` класс, который является производным от `ProjectNode` класса. `ProjectNode` Базовый класс обрабатывает следующие задачи создания проекта:  
  
-   Копирует файл шаблона проекта, *SimpleProject.myproj*, в папку нового проекта. Копия переименовывается в соответствии с именем, введенным в **новый проект** диалоговое окно. `ProjectGuid` Значение свойства заменяется на новый идентификатор GUID.  
  
-   Обходит элементы MSBuild файла шаблона проекта *SimpleProject.myproj*и ищет `Compile` элементов. Для каждого `Compile` целевого файла, файл копируется в папку нового проекта.  
  
 Производные `SimpleProjectNode` класс выполняет эти задачи:  
  
-   Позволяет значков для узлов проекта и файла в **обозревателе решений** для создания или выбран.  
  
-   Включает дополнительный проект замены параметров шаблона должны быть указаны.  
  
### <a name="to-extend-the-projectnode-class"></a>Чтобы расширить класс ProjectNode  
  
1.  Добавьте класс с именем `SimpleProjectNode.cs`.  
  
2.  Замените существующий код следующим кодом:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Project;  
  
    namespace SimpleProject  
    {  
        public class SimpleProjectNode : ProjectNode  
        {  
            private SimpleProjectPackage package;  
  
            public SimpleProjectNode(SimpleProjectPackage package)  
            {  
                this.package = package;  
            }  
            public override Guid ProjectGuid  
            {  
                get { return SimpleProjectPackage.guidSimpleProjectFactory; }  
            }  
            public override string ProjectType  
            {  
                get { return "SimpleProjectType"; }  
            }  
  
            public override void AddFileFromTemplate(  
                string source, string target)  
            {  
                this.FileTemplateProcessor.UntokenFile(source, target);  
                this.FileTemplateProcessor.Reset();  
            }  
        }  
    }  
    ```  
  
 Это `SimpleProjectNode` реализацию класса имеет эти переопределенные методы:  
  
-   `ProjectGuid`, который возвращает идентификатор GUID фабрики проектов.  
  
-   `ProjectType`, который возвращает локализованное имя типа проекта.  
  
-   `AddFileFromTemplate`, который копирует выбранные файлы из папки шаблона к проекту назначения. Дополнительно этот метод реализуется в одном из следующих разделов.  
  
 `SimpleProjectNode` Конструктор, например `SimpleProjectFactory` конструктор, кэширует `SimpleProjectPackage` ссылку в скрытом поле для последующего использования.  
  
 Для подключения `SimpleProjectFactory` класс `SimpleProjectNode` класса, необходимо создать экземпляр нового `SimpleProjectNode` в `SimpleProjectFactory.CreateProject` метод и кэшировать его в скрытом поле для последующего использования.  
  
### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Для подключения класс фабрики проекта и класс узла  
  
1.  В *SimpleProjectFactory.cs* добавьте следующие `using` инструкции:  
  
    ```csharp  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  Замените `SimpleProjectFactory.CreateProject` метода, используя следующий код.  
  
    ```csharp  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
## <a name="test-the-projectnode-class"></a>Класс ProjectNode теста  
 Протестируйте свою фабрику проекта, чтобы понять, каким он иерархии проекта.  
  
### <a name="to-test-the-projectnode-class"></a>Чтобы протестировать класс ProjectNode  
  
1.  Нажмите клавишу **F5** , чтобы начать отладку. В экспериментальном экземпляре создайте новый SimpleProject.  
  
2.  Visual Studio следует вызывать фабрикой проекта для создания проекта.  
  
3.  Закройте экспериментальный экземпляр Visual Studio.  
  
## <a name="add-a-custom-project-node-icon"></a>Добавить значок узла пользовательского проекта  
 Значок узла проекта в одном из предыдущих разделов — значок по умолчанию. Его можно изменить для пользовательского значка.  
  
### <a name="to-add-a-custom-project-node-icon"></a>Чтобы добавить значок узла пользовательского проекта  
  
1.  В **ресурсы** папки, добавьте к файлу точечного рисунка с именем *SimpleProjectNode.bmp*.  
  
2.  В **свойства** windows, уменьшить точечного рисунка 16 x 16 пикселей. Сделайте различение растрового изображения.  
  
     ![Команда простого проекта](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  В **свойства** измените **действие при сборке** растрового изображения для **внедренный ресурс**.  
  
4.  В *SimpleProjectNode.cs*, добавьте следующий `using` инструкции:  
  
    ```csharp  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  Добавьте следующие статические поля и конструктор для `SimpleProjectNode` класса.  
  
    ```csharp  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  Добавьте следующее свойство в начале `SimpleProjectNode` класса.  
  
    ```csharp  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Конструктор экземпляра, замените следующий код.  
  
    ```csharp  
    public SimpleProjectNode(SimpleProjectPackage package)  
    {  
        this.package = package;  
  
        imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
        foreach (Image img in imageList.Images)  
        {  
            this.ImageHandler.AddImage(img);  
        }  
    }  
    ```  
  
 Во время статической конструкции `SimpleProjectNode` извлекает узел проекта растрового изображения из ресурсов манифеста сборки и кэширует его в скрытом поле для последующего использования. Обратите внимание, что синтаксис <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> путь к изображению. Чтобы просмотреть имена ресурсов манифеста, внедренных в сборку, используйте <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> метод. Если этот метод применяется к `SimpleProject` сборки, результаты должны выглядеть следующим образом:  
  
-   *SimpleProject.Resources.resources*  
  
-   *VisualStudio.Project.resources*  
  
-   *SimpleProject.VSPackage.resources*  
  
-   *Resources.imagelis.bmp*  
  
-   *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*  
  
-   *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*  
  
-   *SimpleProject.Resources.SimpleProjectNode.bmp*  
  
 Во время построения экземпляра `ProjectNode` базового класса загружает *Resources.imagelis.bmp*, в которой внедряются часто используется 16 x 16 точечных рисунков из *Resources\imagelis.bmp*. Этот список точечного рисунка, предоставляется `SimpleProjectNode` как `ImageHandler.ImageList`. `SimpleProjectNode` Битовая карта узла проекта добавляет к списку. Смещение растрового изображения узел проекта в списке изображений кэшируется для последующего использования в качестве значения открытого `ImageIndex` свойство. Visual Studio использует это свойство, чтобы определить, какие растрового изображения, отображаемого в качестве значка узла проекта.  
  
## <a name="test-the-custom-project-node-icon"></a>Значок узла пользовательского проекта тестирования  
 Протестируйте свою фабрику проекта, чтобы понять, каким он иерархии проекта, в которой значок узла данного пользовательского проекта.  
  
### <a name="to-test-the-custom-project-node-icon"></a>Для тестирования значок узла пользовательского проекта  
  
1.  Начать отладку и в экспериментальном экземпляре создайте новый SimpleProject.  
  
2.  Обратите внимание, что в проекте только что созданный *SimpleProjectNode.bmp* используется в качестве значка узла проекта.  
  
     ![Простой проект новый узел проекта](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Откройте *Program.cs* в редакторе кода. Вы увидите исходный код, похожий на приведенный ниже.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Обратите внимание на то, что параметры шаблона $nameSpace$ и $className$ нет новых значений. Вы узнаете, как реализовать замена параметров шаблона в следующем разделе.  
  
## <a name="substitute-template-parameters"></a>Замена параметров шаблона  
 В предыдущем разделе, можно зарегистрировать шаблона проекта в Visual Studio с помощью `ProvideProjectFactory` атрибута. Регистрация путь к папке шаблона таким образом позволяет включить подстановку параметров базового шаблона, переопределение и расширение `ProjectNode.AddFileFromTemplate` класса. Дополнительные сведения см. в разделе [Создание нового проекта: взгляд изнутри, часть вторая](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Теперь добавьте код замены `AddFileFromTemplate` класса.  
  
### <a name="to-substitute-template-parameters"></a>Для замены параметров шаблона  
  
1.  В *SimpleProjectNode.cs* добавьте следующие `using` инструкции.  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Замените `AddFileFromTemplate` метода, используя следующий код.  
  
    ```csharp  
    public override void AddFileFromTemplate(  
        string source, string target)  
    {  
        string nameSpace =   
            this.FileTemplateProcessor.GetFileNamespace(target, this);  
        string className = Path.GetFileNameWithoutExtension(target);  
  
        this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
        this.FileTemplateProcessor.AddReplace("$className$", className);  
  
        this.FileTemplateProcessor.UntokenFile(source, target);  
        this.FileTemplateProcessor.Reset();  
    }  
    ```  
  
3.  Установите точку останова в методе, сразу после `className` оператор присваивания.  
  
 Операторы присваивания определите приемлемые значения для пространства имен и имя нового класса. Два `ProjectNode.FileTemplateProcessor.AddReplace` вызовы методов замените соответствующие значения параметров шаблона с помощью этих новых значений.  
  
## <a name="test-the-template-parameter-substitution"></a>Тестирование замена параметров шаблона  
 Теперь можно протестировать замена параметров шаблона.  
  
### <a name="to-test-the-template-parameter-substitution"></a>Для тестирования замена параметров шаблона  
  
1.  Начать отладку и в экспериментальном экземпляре создайте новый SimpleProject.  
  
2.  Выполнение остановится в точке останова в `AddFileFromTemplate` метод.  
  
3.  Проверить значения для `nameSpace` и `className` параметров.  
  
    -   `nameSpace` Получает значение \<RootNamespace > элемент в *\Templates\Projects\SimpleProject\SimpleProject.myproj* файл шаблона проекта. В этом случае используется значение `MyRootNamespace`.  
  
    -   `className` Получает значение имени класса источника файла без расширения имени файла. В этом случае первый файл копируются в папку назначения является *AssemblyInfo.cs*; таким образом, значение className `AssemblyInfo`.  
  
4.  Удалите точку останова и нажмите клавишу **F5** следует продолжить выполнение.  
  
     Visual Studio следует завершить создание проекта.  
  
5.  Откройте *Program.cs* в редакторе кода. Вы увидите исходный код, похожий на приведенный ниже.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace MyRootNamespace  
    {  
        public class Program  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Обратите внимание, что пространство имен теперь `MyRootNamespace` и имя класса — теперь `Program`.  
  
6.  Начните отладку проекта. Новый проект должен компиляции, запуска и отображение «Hello VSX!!!» в окне консоли.  
  
     ![Команда Simple Project](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 Поздравляем! Реализации системы базового управляемого проекта.