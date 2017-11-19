---
title: "Создание базового проекта системы, часть 1 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: "47"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e61c0d681dac52e85c3854325ee20ada29d74d4c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-basic-project-system-part-1"></a>Создание базового проекта системы, часть 1
В Visual Studio проекты — это контейнеры, которые разработчики используют для организации файлов исходного кода и других ресурсов. Проекты отображаются как дочерние элементы решений в **обозревателе решений**. Проекты позволяют организовать, построения, отладки и развертывания исходного кода и создавать ссылки на Web services, баз данных и другие ресурсы.  
  
 Проекты, определяются в файлах проектов, например CSPROJ-файл в проекте Visual C#. Можно создать проект собственного типа, имеет собственную расширение имени файла проекта. Дополнительные сведения о типах проектов см. в разделе [типы проектов](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Если вам нужно расширить с помощью пользовательского типа проектов Visual Studio, настоятельно рекомендуется использование [система проектов Visual Studio](https://github.com/Microsoft/VSProjectSystem) которого имеет ряд преимуществ по сравнению с создается система проекта с нуля:  
>   
>  -   Упрощает адаптацию.  Даже в системе базового проекта требуется десятков тысяч строк кода.  Используя CPS уменьшает затраты на адаптации щелчков, прежде чем приступить к настройке его в соответствии с потребностями.  
> -   Упрощает обслуживание.  За счет использования CPS, только нужно хранить собственные сценарии.  Мы обрабатывать поддержку всех инфраструктуры системы проекта.  
>   
>  Требуется целевой версии Visual Studio более ранней, чем Visual Studio 2013, вы не сможете использовать CPS в расширение Visual Studio.  Если это так, в данном пошаговом руководстве является удобным инструментом для начала.  
  
 В этом пошаговом руководстве показано, как создать тип проекта, который имеет .myproj расширение имени файла проекта. В этом пошаговом руководстве занимает в существующей системе проектов Visual C#.  
  
> [!NOTE]
>  Дополнительные примеры проектов расширения см. в разделе [примеры VSSDK](http://aka.ms/vs2015sdksamples).  
  
 В этом пошаговом руководстве рассматриваются способы выполнения этих задач:  
  
-   Создание базового проекта типа.  
  
-   Создание базового проекта шаблона.  
  
-   Зарегистрируйте шаблон проекта Visual Studio.  
  
-   Создать экземпляр проекта, открыв **новый проект** диалоговое окно, а затем с помощью шаблона.  
  
-   Создайте фабрику проекта для вашей системы проекта.  
  
-   Создайте узел проекта в системе проекта.  
  
-   Добавьте настраиваемые значки для системы проектов.  
  
-   Реализуйте подстановку параметров базового шаблона.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Кроме того, необходимо загрузить исходный код для [Managed Package Framework для проектов](http://mpfproj12.codeplex.com/). Извлеките файл в расположении, доступном для решения, которое вы собираетесь создать.  
  
## <a name="creating-a-basic-project-type"></a>Создание базового проекта типа  
 Создайте проект VSIX C# с именем **SimpleProject**. (**Файл, создать, проект** и затем **пакет Visual Studio C#, расширяемость,**). Добавить шаблон элемента проекта пакета Visual Studio (в обозревателе решений щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**, а затем перейдите к **расширяемость / пакет Visual Studio**). Назовите файл **SimpleProjectPackage**.  
  
## <a name="creating-a-basic-project-template"></a>Создание базового проекта шаблона  
 Теперь вы можете изменить этот базовый VSPackage для реализации новый тип проекта .myproj. Чтобы создать проект, основанный на типе проекта .myproj, Visual Studio должен знать, какие файлы, ресурсы и ссылки для добавления в новый проект. Для предоставления этих данных, поместите файлы проекта в папке проекта шаблона. Когда пользователь использует .myproj проекта для создания проекта, файлы копируются в новый проект.  
  
#### <a name="to-create-a-basic-project-template"></a>Создание базового проекта шаблона  
  
1.  Добавьте три папки в проект, в другой: **Templates\Projects\SimpleProject**. (В **обозревателе решений**, щелкните правой кнопкой мыши **SimpleProject** узел проекта, выберите пункт **добавить**, а затем нажмите кнопку **новую папку**. Назовите папку `Templates`. В **шаблоны** папки, добавьте папку с именем `Projects`. В **проекты** папки, добавьте папку с именем `SimpleProject`.)  
  
2.  В **Projects\SimpleProject** папку добавить файл значка с именем `SimpleProject.ico`. При нажатии кнопки **добавить**, открывается редактор значков.  
  
3.  Сделайте различение значок. Этот значок появится в **новый проект** диалоговое окно «» далее в этом пошаговом руководстве.  
  
     ![Значок простого проекта](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  Значок сохраните и закройте редактор значков.  
  
5.  В **Projects\SimpleProject** папки, добавьте **класса** элемент с именем `Program.cs`.  
  
6.  Замените существующий код следующие строки.  
  
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
    >  Это не конечная форма кода Program.cs; Параметры замены будет обрабатываться в более позднем этапе. Может появиться ошибки компиляции, но пока файла **BuildAction** — **содержимого**, можно для построения и запуска проекта обычным образом.  
  
1.  Сохраните файл.  
  
2.  Скопируйте файл AssemblyInfo.cs из **свойства** папки **Projects\SimpleProject** папки.  
  
3.  В **Projects\SimpleProject** папку добавить XML-файл с именем `SimpleProject.myproj`.  
  
    > [!NOTE]
    >  Расширение имени файла для всех проектов этого типа является .myproj. Если вы хотите изменить его, необходимо изменить его везде, где упоминается в этом пошаговом руководстве.  
  
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
  
6.  В **свойства** задайте **действие при построении** AssemblyInfo.cs, Program.cs, SimpleProject.ico и SimpleProject.myproj для **содержимого**и задайте их  **Включить в VSIX** свойства **True**.  
  
 Этот шаблон проекта описывает основные проекта Visual C# с отладочной конфигурации и конфигурации выпуска. Проект включает два исходных файлов, AssemblyInfo.cs и Program.cs и несколько сборки ссылок. При создании проекта из шаблона ProjectGuid значение автоматически заменяется новый идентификатор GUID.  
  
 В **обозревателе решений**, развернутом **шаблоны** папки должна выглядеть следующим образом:  
  
 Шаблоны  
  
 Проекты  
  
 SimpleProject  
  
 AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>Создание фабрики базового проекта  
 Необходимо указать расположение папки шаблона проекта Visual Studio. Для этого добавьте атрибут в класс VSPackage, реализующий фабрики проектов, чтобы расположение шаблона записывается в системный реестр, при построении пакета VSPackage. Начните с создания базового проекта фабрику, которая определяется GUID фабрики проектов. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут для подключения к SimpleProjectPackage класса фабрики проектов.  
  
#### <a name="to-create-a-basic-project-factory"></a>Для создания фабрики базового проекта  
  
1.  Откройте SimpleProjectPackageGuids.cs в редакторе кода.  
  
2.  Создание GUID для фабрики проект (на **средства** меню, нажмите кнопку **создать GUID**), или использовать в следующем примере. Добавьте в класс SimpleProjectPackageGuids идентификаторы GUID. Идентификаторы GUID должен быть в виде идентификатора GUID и строковый формат. Итоговый код должен выглядеть примерно так.  
  
    ```  
    static class SimpleProjectPackageGuids  
    {  
        public const string guidSimpleProjectPkgString =   
            "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
        public const string guidSimpleProjectCmdSetString =   
            "72c23e1d-f389-410a-b5f1-c938303f1391";  
        public const string guidSimpleProjectFactoryString =   
            "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
        public static readonly Guid guidSimpleProjectCmdSet =   
            new Guid(guidSimpleProjectCmdSetString);  
        public static readonly Guid guidSimpleProjectFactory =   
            new Guid(guidSimpleProjectFactoryString);  
    }  
    ```  
  
3.  Добавьте в начало класса **SimpleProject** папку с именем `SimpleProjectFactory.cs`.  
  
4.  Добавьте следующие операторы using:  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Добавьте в класс SimpleProjectFactory атрибут Guid. Значение атрибута — новый GUID фабрики проектов.  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Теперь можно зарегистрировать шаблон проекта.  
  
#### <a name="to-register-the-project-template"></a>Чтобы зарегистрировать шаблон проекта  
  
1.  Добавьте в SimpleProjectPackage.cs, <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибута к классу SimpleProjectPackage следующим образом.  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
     Перестроение регистрирует шаблон проекта.  
  
 Параметры `defaultProjectExtension` и `possibleProjectExtensions` присваивается расширение имени файла проекта (.myproj). `projectTemplatesDirectory` Параметра равным относительный путь к папке «Шаблоны». Во время сборки этот путь будет преобразовать полное построение и добавляется в реестр для регистрации в системе проекта.  
  
## <a name="testing-the-template-registration"></a>Тестирование регистрацию шаблона  
 Регистрацию шаблона расположение папки шаблона проекта среда Visual Studio, Visual Studio отображать имя шаблона и значок в **новый проект** диалоговое окно.  
  
#### <a name="to-test-the-template-registration"></a>Чтобы проверить регистрацию шаблона  
  
1.  Нажмите клавишу F5 для запуска отладки экспериментальный экземпляр Visual Studio.  
  
2.  В экспериментальном экземпляре создайте новый проект типа созданного проекта. В **новый проект** диалоговое окно, вы увидите **SimpleProject** под **установленные шаблоны**.  
  
 Теперь у вас фабрики проектов, в которой зарегистрирован. Он еще не удается создать проект. Проект пакета и проекта фабрики совместной работы для создания и инициализации проекта.  
  
## <a name="add-the-managed-package-framework-code"></a>Добавьте код Managed Package Framework  
 Реализуйте соединения пакета проекта и фабрики проектов.  
  
-   Импортируйте файлы исходного кода для Managed Package Framework.  
  
    1.  Выгрузить проект SimpleProject (в **обозревателе решений**, выберите узел проекта и в контекстном меню щелкните **выгрузить проект**.) и откройте файл проекта в XML-редакторе.  
  
    2.  Добавьте следующие блоки в файл проекта (непосредственно над \<импорта > блоков). Задать расположение файла ProjectBase.files в только что загруженном коде Managed Package Framework ProjectBasePath. Может потребоваться добавить обратную косую черту в имени пути. Если этого не сделать, не удастся найти Managed Package Framework код проекта.  
  
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
  
        -   Microsoft.VisualStudio.Designer.Interfaces (в \<установки VSSDK > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Для инициализации фабрики проектов  
  
1.  Добавьте следующие строки в файле SimpleProjectPackage.cs `using` инструкции.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Производные `SimpleProjectPackage` класса из `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Регистрация фабрики проектов. Добавьте следующую строку в `SimpleProjectPackage.Initialize` метод, сразу после `base.Initialize`.  
  
    ```  
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
  
5.  В SimpleProjectFactory.cs, добавьте следующий `using` инструкции после существующего `using` инструкции.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Производные `SimpleProjectFactory` класса из `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Добавьте следующий метод фиктивное `SimpleProjectFactory` класса. Этот метод реализуется в одном из следующих разделов.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Добавьте следующие поля и конструктор для `SimpleProjectFactory` класса. Это `SimpleProjectPackage` ссылка кэшируется в закрытом поле, чтобы он может использоваться при установке сайта поставщика услуг.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
## <a name="testing-the-project-factory-implementation"></a>Тестирование реализации фабрики проектов  
 Проверка вызывается конструктор для реализации фабрики проектов.  
  
#### <a name="to-test-the-project-factory-implementation"></a>Для тестирования реализации фабрики проектов  
  
1.  В файле SimpleProjectFactory.cs установить точку останова на следующую строку в `SimpleProjectFactory` конструктора.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Нажмите клавишу F5, чтобы запустить экспериментальный экземпляр Visual Studio.  
  
3.  В экспериментальном экземпляре Начните создание нового проекта. В **новый проект** установите флажок SimpleProject тип проекта, а затем нажмите кнопку **ОК**. Выполнение прекратится в точке останова.  
  
4.  Удалите точку останова и остановить отладку. Поскольку мы имеют еще не создан узел проекта, код создания проекта по-прежнему создает исключения.  
  
## <a name="extending-the-project-node-class"></a>Расширение класса узла проекта  
 Теперь вы можете реализовать `SimpleProjectNode` класс, который является производным от `ProjectNode` класса. `ProjectNode` Базовый класс обрабатывает следующие задачи создания проекта:  
  
-   Копирует файл шаблона проекта SimpleProject.myproj, в папку нового проекта. Копия переименовывается в соответствии с именем, введенным в **новый проект** диалоговое окно. `ProjectGuid` Значение свойства заменяется на новый идентификатор GUID.  
  
-   Обходит элементы MSBuild файла шаблона проекта SimpleProject.myproj и ищет `Compile` элементов. Для каждого `Compile` целевой файл скопирует файл в папку проекта.  
  
 Производные `SimpleProjectNode` класс обрабатывает эти задачи:  
  
-   Включает значков для узлов проекта и файла в **обозревателе решений** для создания или выбран.  
  
-   Включает дополнительный проект замены параметров шаблона должен быть задан.  
  
#### <a name="to-extend-the-project-node-class"></a>Чтобы расширить класс узла проекта  
  
1.  
  
2.  Добавьте класс с именем `SimpleProjectNode.cs`.  
  
3.  Замените существующий код следующим кодом:  
  
    ```  
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
                get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
-   `ProjectGuid`, который возвращает GUID фабрики проектов.  
  
-   `ProjectType`, который возвращает локализованное имя типа проекта.  
  
-   `AddFileFromTemplate`, который копирует выбранные файлы в папке шаблона в целевой проект. Этот метод реализуется дальнейшей в одном из следующих разделов.  
  
 `SimpleProjectNode` Конструктора, таких как `SimpleProjectFactory` кэширует конструктор, `SimpleProjectPackage` ссылка в закрытое поле для дальнейшего использования.  
  
 Для подключения `SimpleProjectFactory` класса `SimpleProjectNode` класса, необходимо создать экземпляр нового `SimpleProjectNode` в `SimpleProjectFactory.CreateProject` метод и кэширует его в закрытом поле для дальнейшего использования.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Для подключения класс фабрики проектов и класс узла  
  
1.  Добавьте следующие строки в файле SimpleProjectFactory.cs `using` инструкции:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  Замените `SimpleProjectFactory.CreateProject` метода, используя следующий код.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
## <a name="testing-the-project-node-class"></a>Тестирование класс узла проекта  
 Тестирование проекта фабрики для просмотра, создает ли иерархии проекта.  
  
#### <a name="to-test-the-project-node-class"></a>Чтобы протестировать класс узла проекта  
  
1.  Нажмите клавишу F5, чтобы начать отладку. В экспериментальном экземпляре создайте новый SimpleProject.  
  
2.  Visual Studio следует вызывать проекта фабрику для создания проекта.  
  
3.  Закройте экспериментальный экземпляр Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Добавление узла значок в виде пользовательских проектов  
 Значок узла проекта в предыдущем разделе отображается значок по умолчанию. Его можно изменить на пользовательский значок.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Чтобы добавить в проект пользовательский узел значок  
  
1.  В **ресурсов** папки, добавьте файл растрового изображения, с именем SimpleProjectNode.bmp.  
  
2.  В **свойства** windows, уменьшить точечный рисунок до 16 на 16 пикселей. Сделайте различение растрового изображения.  
  
     ![Команда простого проекта](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  В **свойства** измените **действие построения** точечного рисунка, который **внедренный ресурс**.  
  
4.  В SimpleProjectNode.cs, добавьте следующий `using` инструкции:  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  Добавьте следующие статические поля и конструктор для `SimpleProjectNode` класса.  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  Добавьте следующее свойство к началу `SimpleProjectNode` класса.  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Конструктор экземпляра, замените следующий код.  
  
    ```  
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
  
 Во время статической конструкции `SimpleProjectNode` извлекает узел проекта точечного рисунка из ресурсов манифеста сборки и кэширует его в закрытом поле для дальнейшего использования. Обратите внимание на синтаксис из <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> путь к изображению. Для просмотра имен ресурсов манифеста, внедренных в сборку, используйте <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> метод. Если этот метод применяется к `SimpleProject` сборки, результаты должны выглядеть следующим образом:  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 Во время создания экземпляра `ProjectNode` Resources.imagelis.bmp, в которой являются внедренными часто используемых растровыми изображениями 16 x 16 из Resources\imagelis.bmp загружает базового класса. Этот список растровое изображение становится доступным `SimpleProjectNode` как ImageHandler.ImageList. `SimpleProjectNode`Добавляет к списку битовой карты узла проекта. Смещение битовой карты узла проекта в список изображений кэшируется для последующего использования в качестве значения открытых `ImageIndex` свойство. Visual Studio использует это свойство, чтобы определить, какие растрового изображения, отображаемого в качестве значка узел проекта.  
  
## <a name="testing-the-custom-project-node-icon"></a>Значок узла пользовательский проект тестирования  
 Тестирование проекта фабрики для просмотра, создает ли проект иерархии, содержащей значка вашего проекта пользовательского узла.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Чтобы проверить значок узла пользовательский проект  
  
1.  Начните отладку и в экспериментальном экземпляре создайте новый SimpleProject.  
  
2.  В только что созданный проект Обратите внимание, что SimpleProjectNode.bmp используется как значок узел проекта.  
  
     ![Простой проект узел нового проекта](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Откройте файл Program.cs в редакторе кода. Вы увидите исходный код, подобный приведенному ниже.  
  
    ```  
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
  
     Обратите внимание, что параметры шаблона $nameSpace$ и $className$ нет новых значений. Вы узнаете, как реализовать замена параметров шаблона в следующем разделе.  
  
## <a name="substituting-template-parameters"></a>Замена параметров шаблона  
 В предыдущем разделе, можно зарегистрировать шаблон проекта в Visual Studio с помощью `ProvideProjectFactory` атрибута. Регистрация путь к папке шаблона таким способом позволяет включить подстановку параметров базового шаблона переопределения и развернув `ProjectNode.AddFileFromTemplate` класса. Дополнительные сведения см. в разделе [Создание нового проекта: В механизме, второй части](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Теперь добавьте код замены `AddFileFromTemplate` класса.  
  
#### <a name="to-substitute-template-parameters"></a>Для замены параметров шаблона  
  
1.  Добавьте следующие строки в файле SimpleProjectNode.cs `using` инструкции.  
  
    ```  
    using System.IO;  
    ```  
  
2.  Замените `AddFileFromTemplate` метода, используя следующий код.  
  
    ```  
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
  
 Операторы присваивания определить приемлемые значения для пространства имен и новое имя класса. Два `ProjectNode.FileTemplateProcessor.AddReplace` вызовы метода замены значения соответствующего параметра шаблона с помощью этих новых значений.  
  
## <a name="testing-the-template-parameter-substitution"></a>Тестирование замена параметров шаблона  
 Теперь можно проверить замена параметров шаблона.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>Чтобы проверить замена параметров шаблона  
  
1.  Начните отладку и в экспериментальном экземпляре создайте новый SimpleProject.  
  
2.  Выполнение останавливается в точке останова `AddFileFromTemplate` метод.  
  
3.  Проверить значения для `nameSpace` и `className` параметров.  
  
    -   `nameSpace`Получает значение \<RootNamespace > в файле шаблона проекта \Templates\Projects\SimpleProject\SimpleProject.myproj элемент. В этом случае значение — «MyRootNamespace».  
  
    -   `className`Получает значение имени класса источника файла без расширения имени файла. В этом случае первый файл копируются в папку назначения является AssemblyInfo.cs; Таким образом значение className равно «AssemblyInfo».  
  
4.  Удалите точку останова и нажмите клавишу F5, чтобы продолжить выполнение.  
  
     Visual Studio необходимо завершить создание проекта.  
  
5.  Откройте файл Program.cs в редакторе кода. Вы увидите исходный код, подобный приведенному ниже.  
  
    ```  
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
  
     Обратите внимание, что пространство имен теперь «MyRootNamespace» и класс теперь называется «Программы».  
  
6.  Начните отладку проекта. Новый проект должен компиляции, запуска и отображение «Hello VSX»!!! в окне консоли.  
  
     ![Команда простого проекта](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 Поздравляем! Реализации системы базовый управляемый проект.