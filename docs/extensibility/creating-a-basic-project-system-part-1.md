---
title: "Создание базового проекта системы, часть 1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "записи системы проектов"
  - "Система проектов"
  - "учебник"
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 47
caps.handback.revision: 47
ms.author: "gregvanl"
manager: "ghogen"
---
# Создание базового проекта системы, часть 1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В Visual Studio проекты — это контейнеры, которые разработчики используют для организации файлов исходного кода и других ресурсов. Проекты отображаются как дочерние элементы решений в **обозревателе решений**. Проекты позволяют организовывать, построения, отладки и развертывания исходного кода и создание ссылок на Web services, баз данных и другие ресурсы.  
  
 Проекты определены в файлах проекта, например в CSPROJ\-файл для проекта Visual C\#. Можно создать проект собственного типа, имеет собственный расширение имени файла проекта. Дополнительные сведения о типах проектов см. в разделе [Типы проектов](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Если необходимо расширить Visual Studio с помощью пользовательского типа проектов, настоятельно рекомендуется использование [Система проектов Visual Studio](https://github.com/Microsoft/VSProjectSystem) которого имеет ряд преимуществ по сравнению с создания проекта системы с нуля:  
>   
>  -   Проще адаптации.  Базовый проект системы требует десятки тысяч строк кода.  Используя CPS сокращает стоимость адаптации несколько щелчков мышью, прежде чем приступить к настройке его в соответствии с потребностями.  
> -   Упрощает обслуживание.  Используя CPS, достаточно для поддержки собственных сценариях.  Рекомендуется обрабатывать ведении инфраструктура системы проекта.  
>   
>  Если требуется целевой версии Visual Studio, старше, чем Visual Studio 2013 не появится возможность использовать CPS в расширение Visual Studio.  Если это так, в этом пошаговом руководстве является хорошим местом для начала.  
  
 В этом пошаговом руководстве показано, как создать тип проекта, который имеет .myproj расширение имени файла проекта. В этом пошаговом руководстве занимает в существующей системе проектов Visual C\#.  
  
> [!NOTE]
>  Пример end\-to\-end полный языка системы проекта см. Образец IronPython глубокое погружение в [Примеры VSSDK](../misc/vssdk-samples.md).  
  
 В этом пошаговом руководстве объясняется, как выполнять эти задачи:  
  
-   Создание базового проекта типа.  
  
-   Создание базового проекта шаблона.  
  
-   Зарегистрируете шаблон проекта Visual Studio.  
  
-   Создайте экземпляр проекта, открыв **Новый проект** диалоговое окно, а затем с помощью шаблона.  
  
-   Создание фабрики проекта для вашей системы проекта.  
  
-   Создайте узел проекта для вашей системы проекта.  
  
-   Добавление настраиваемых значков для системы проектов.  
  
-   Реализуйте базовый шаблон подстановку параметров.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Также необходимо загрузить исходный код для [управляемых платформа пакетов для проектов](http://mpfproj12.codeplex.com/). Распакуйте файл в расположение, доступное решение, которое вы собираетесь создать.  
  
## Создание базового проекта типа  
 Создайте проект VSIX C\# с именем **SimpleProject**. \(**Файл, создать, проект** и **пакет Visual Studio C\#, расширяемость,**\). Добавление шаблона элемента проекта пакета Visual Studio \(в обозревателе решений щелкните правой кнопкой мыши узел проекта и выберите **Добавить\-новый элемент**, а затем перейдите к **расширения или пакета Visual Studio**\). Присвойте файлу имя **SimpleProjectPackage**.  
  
## Создание базового проекта шаблона  
 Теперь вы можете изменить этот базовый VSPackage реализовать новый тип проекта .myproj. Чтобы создать проект, основанный на типе проекта .myproj, Visual Studio должен знать, какие файлы, ресурсы и ссылки для добавления в новый проект. Чтобы предоставить эти сведения, поместите файлы проекта в папке проекта шаблона. Когда пользователь использует .myproj проекта для создания проекта, файлы копируются в новый проект.  
  
#### Создание базового проекта шаблона  
  
1.  Добавьте три папки в проект, в другой: **Templates\\Projects\\SimpleProject**. \(В **Обозреватель решений**, щелкните правой кнопкой мыши **SimpleProject** узел проекта, выберите пункт **Добавить**, а затем нажмите кнопку **новую папку**. Назовите папку `Templates`. В **шаблоны** папки, добавить папку с именем `Projects`. В **проекты** папки, добавить папку с именем `SimpleProject`.\)  
  
2.  В **Projects\\SimpleProject** добавьте файл значка с именем `SimpleProject.ico`. При нажатии кнопки **Добавить**, откроется редактор значков.  
  
3.  Сделать специальный значок. Этот значок появляется в **Новый проект** диалоговое окно «» далее в этом пошаговом руководстве.  
  
     ![Значок: значок простого проекта](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  Значок сохраните и закройте редактор значков.  
  
5.  В **Projects\\SimpleProject** папки, добавить **класса** элемент с именем `Program.cs`.  
  
6.  Замените существующий код следующие строки.  
  
    ```c#  
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
    >  Это не конечная форма кода Program.cs; Параметры замены будут обработаны позже. Может появиться ошибки компиляции, но при условии, что и файл **BuildAction** — **содержимого**, вы сможете построить и запустить проект как обычно.  
  
1.  Сохраните файл.  
  
2.  Скопируйте файл AssemblyInfo.cs **Свойства** папки **Projects\\SimpleProject** папки.  
  
3.  В **Projects\\SimpleProject** добавьте XML\-файл с именем `SimpleProject.myproj`.  
  
    > [!NOTE]
    >  Расширение имени файла для всех проектов этого типа — .myproj. Если вы хотите изменить его, необходимо изменить его везде, где оно встречается в пошаговом руководстве.  
  
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
  
6.  В **Свойства** установите **Действие при построении** AssemblyInfo.cs, Program.cs, SimpleProject.ico и SimpleProject.myproj для **содержимого**, и задайте их **Включить в VSIX** свойства **True**.  
  
 Этот шаблон описывает основные Visual C\# проект с отладочной конфигурации и конфигурации выпуска. Проект содержит два исходных файлов, AssemblyInfo.cs и Program.cs и несколько сборки ссылки. При создании проекта из шаблона ProjectGuid значение автоматически заменяется новый идентификатор GUID.  
  
 В **обозревателе решений**, расширенный **шаблоны** папка должна выглядеть следующим образом:  
  
 Шаблоны  
  
 Проекты  
  
 SimpleProject  
  
 Файл AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## Создание базового проекта фабрики  
 Необходимо указать расположение папки шаблона проекта Visual Studio. Для этого добавьте атрибут в класс VSPackage, который реализует фабрики проектов, чтобы расположение шаблона записывается в системный реестр при построении VSPackage. Начните с создания базового проекта фабрику, которая определяется GUID фабрики проекта. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут для подключения к SimpleProjectPackage класса фабрики проектов.  
  
#### Чтобы создать фабрику базового проекта  
  
1.  Откройте SimpleProjectPackageGuids.cs в редакторе кода.  
  
2.  Создание GUID для фабрики проекта \(на **средства** меню, щелкните **Создать GUID**\), или использовать в следующем примере. Добавьте в класс SimpleProjectPackageGuids идентификаторы GUID. Идентификаторы GUID должны быть в виде идентификатора GUID и формат строки. Итоговый код должен выглядеть примерно так.  
  
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
  
5.  Добавьте в класс SimpleProjectFactory атрибут Guid. Значение атрибута является новой фабрики проекта GUID.  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Теперь можно зарегистрировать шаблон проекта.  
  
#### Чтобы зарегистрировать шаблон проекта  
  
1.  Добавьте в SimpleProjectPackage.cs, <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут в класс SimpleProjectPackage следующим образом.  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
     Перестроение регистрирует шаблон проекта.  
  
 Параметры `defaultProjectExtension` и `possibleProjectExtensions` присваивается расширение имени файла проекта \(.myproj\).`projectTemplatesDirectory` Параметру присваивается относительный путь к папке шаблонов. Во время сборки этот путь будет преобразовать полное построение и добавляется в реестр для регистрации в системе проектов.  
  
## Тестирование регистрации шаблона  
 Регистрация шаблона среда Visual Studio расположение папки шаблона проекта, чтобы Visual Studio можно отображать имя шаблона и значок в **Новый проект** диалоговое окно.  
  
#### Чтобы проверить регистрацию шаблона  
  
1.  Нажмите клавишу F5, чтобы запустить отладку в экспериментальном экземпляре Visual Studio.  
  
2.  В экспериментальном экземпляре создайте новый проект из типа созданного проекта. В **Новый проект** увидите диалогового **SimpleProject** под **Установленные шаблоны**.  
  
 Теперь у вас есть проект фабрику, которая регистрируется. Он еще не удается создать проект. Проект пакета и фабрики проекта совместно для создания и инициализации проекта.  
  
## Добавьте код, платформа управляемых пакетов  
 Реализация соединения пакета проекта и фабрики проектов.  
  
-   Импорт файлов исходного кода для платформа управляемых пакетов.  
  
    1.  Выгрузить проект SimpleProject \(в **обозревателе решений**, выберите узел проекта и в контекстном меню щелкните **Выгрузить проект**.\) и откройте файл проекта в XML\-редакторе.  
  
    2.  Добавьте следующие блоки файл проекта \(непосредственно над блоков \< Import \>\). Задать расположение файла ProjectBase.files в загруженный код платформа управляемых пакетов ProjectBasePath. Может потребоваться добавить обратную косую черту в пути. Если этого не сделать, проект не удастся найти кода управляемых пакета .NET Framework.  
  
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
  
        -   Microsoft.VisualStudio.Designer.Interfaces \(в \\VisualStudioIntegration\\Common\\Assemblies\\v2.0 \< VSSDK установки \>\)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### Для инициализации фабрики проекта  
  
1.  Добавьте следующий код в файле SimpleProjectPackage.cs `using` инструкции.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Производные `SimpleProjectPackage` класса `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Зарегистрируйте фабрику проекта. Добавьте следующую строку в `SimpleProjectPackage.Initialize` метод, сразу после `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Реализация абстрактных свойства `ProductUserContext`:  
  
    ```c#  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  Добавьте следующий код в SimpleProjectFactory.cs, `using` инструкции после существующего `using` инструкции.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Производные `SimpleProjectFactory` класса `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Добавьте следующий метод фиктивный `SimpleProjectFactory` класса. Этот метод реализуется в одном из следующих разделов.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Добавьте следующие поля и конструктор для `SimpleProjectFactory` класса. Это `SimpleProjectPackage` ссылку кэшируется в скрытом поле, чтобы он может использоваться при установке сайта поставщика услуг.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
## Тестирование реализации фабрики проекта  
 Проверка вызывается конструктор для реализации фабрики проекта.  
  
#### Чтобы протестировать реализацию фабрики проекта  
  
1.  В файле SimpleProjectFactory.cs установить точку останова на следующую строку в `SimpleProjectFactory` конструктора.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Нажмите клавишу F5, чтобы запустить экспериментальный экземпляр Visual Studio.  
  
3.  В экспериментальном экземпляре начнете создание нового проекта. В **Новый проект** диалоговом SimpleProject тип проекта, а затем нажмите кнопку **ОК**. Выполнение прекратится в точке останова.  
  
4.  Удалите точку останова и остановить отладку. Поскольку мы не создан узел проекта еще, код создания проекта по\-прежнему создает исключения.  
  
## Расширение класса узла проекта  
 Теперь можно реализовать `SimpleProjectNode` класс, который является производным от `ProjectNode` класса.`ProjectNode` Базовый класс обрабатывает следующие задачи создания проекта:  
  
-   Копирует файл шаблона проекта SimpleProject.myproj, в папку нового проекта. Копия переименовывается в соответствии с именем, введенным в **Новый проект** диалоговое окно.`ProjectGuid` Значение заменяется на новый идентификатор GUID.  
  
-   Обходит элементы MSBuild файл шаблона проекта SimpleProject.myproj и ищет `Compile` элементы. Для каждого `Compile` целевого файла копирует файл в папку нового проекта.  
  
 Производный `SimpleProjectNode` класс выполняет следующие задачи:  
  
-   Позволяет значков для узлов проекта и файла в **обозревателе решений** для создания или выбран.  
  
-   Включает дополнительный проект замены параметров шаблона должен быть задан.  
  
#### Чтобы расширить класс узла проекта  
  
1.  
  
2.  Добавьте класс с именем `SimpleProjectNode.cs`.  
  
3.  Замените существующий код следующим кодом.  
  
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
  
-   `AddFileFromTemplate`, который копирует выбранные файлы из папки шаблонов целевой проект. Этот метод реализуется Дополнительно в одном из следующих разделов.  
  
 `SimpleProjectNode` Конструктор, например `SimpleProjectFactory` кэширует конструктор, `SimpleProjectPackage` ссылку на частное поле для дальнейшего использования.  
  
 Для подключения `SimpleProjectFactory` класса `SimpleProjectNode` класса, необходимо создать новый `SimpleProjectNode` в `SimpleProjectFactory.CreateProject` метод и кэшировать его в скрытом поле для дальнейшего использования.  
  
#### Подключение проекта вспомогательный класс и класс узла  
  
1.  Добавьте следующий код в файле SimpleProjectFactory.cs `using` инструкции:  
  
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
  
## Тестирование класса узла проекта  
 Тестирование проекта фабрики для просмотра, создает ли иерархии проекта.  
  
#### Чтобы протестировать класс узла проекта  
  
1.  Нажмите клавишу F5, чтобы начать отладку. В экспериментальном экземпляре создайте новый SimpleProject.  
  
2.  Visual Studio следует вызывать проекта фабрику для создания проекта.  
  
3.  Закройте экспериментальный экземпляр Visual Studio.  
  
## Добавление значка узел пользовательский проект  
 Значок узла проекта в предыдущем разделе находится значок по умолчанию. Его можно изменить на пользовательский значок.  
  
#### Чтобы добавить значок узла пользовательский проект  
  
1.  В **ресурсов** папки, добавьте файл точечного рисунка, с именем SimpleProjectNode.bmp.  
  
2.  В **Свойства** windows, уменьшить точечного рисунка 16 x 16 пикселей. Сделать различение точечного рисунка.  
  
     ![Команда простого проекта](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  В **Свойства** измените **действие построения** точечного рисунка, который **внедренный ресурс**.  
  
4.  Добавьте следующий код в SimpleProjectNode.cs, `using` инструкции:  
  
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
  
6.  Добавьте следующее свойство в начало `SimpleProjectNode` класса.  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Замените конструктор экземпляра с помощью следующего кода.  
  
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
  
 Во время создания статического `SimpleProjectNode` извлекает узел проекта точечный рисунок из ресурсам манифеста сборки и кэширует его в закрытом поле для дальнейшего использования. Обратите внимание на синтаксис из <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> путь к изображению. Чтобы просмотреть имена ресурсов манифеста, внедренного в сборку, используйте <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> метод. Если этот метод применяется к `SimpleProject` сборки, результаты должны выглядеть следующим образом:  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 Во время создания экземпляра `ProjectNode` Resources.imagelis.bmp, в которой находятся внедренные часто используемых точечных рисунков 16 x 16 из Resources\\imagelis.bmp загружает базового класса. Этот список растровое изображение становится доступным `SimpleProjectNode` как ImageHandler.ImageList.`SimpleProjectNode` Добавляет к списку битовой карты узла проекта. Смещение изображения узла проекта в списке изображений кэшируется для последующего использования в качестве значения открытых `ImageIndex` свойство. Visual Studio использует это свойство, чтобы определить, какие точечный рисунок в качестве значка узел проекта.  
  
## Значок узла пользовательский проект тестирования  
 Тестирование проекта фабрики для просмотра, создает ли проект иерархию, в которой значок узла ваш пользовательский проект.  
  
#### Чтобы проверить пользовательский проект значок узла  
  
1.  Начните отладку, а в экспериментальном экземпляре создайте новый SimpleProject.  
  
2.  В только что созданный проект Обратите внимание, что SimpleProjectNode.bmp используется как значок узел проекта.  
  
     ![Простой проект Узел нового проекта](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Откройте файл Program.cs в редакторе кода. Вы должны увидеть исходный код, подобный приведенному ниже.  
  
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
  
     Обратите внимание, что параметры шаблона $nameSpace$ и $className$ нет новых значений. Вы узнаете, как реализовать подстановку параметров шаблона в следующем разделе.  
  
## Замена параметров шаблона  
 В предыдущем разделе, можно зарегистрировать шаблон проекта в Visual Studio с помощью `ProvideProjectFactory` атрибута. Регистрация путь к папке шаблона таким способом позволяет включить подстановку параметров базового шаблона переопределение и развернув `ProjectNode.AddFileFromTemplate` класса. Для получения дополнительной информации см. [Создание нового проекта: За кулисами, часть 2](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md).  
  
 Теперь добавьте замены `AddFileFromTemplate` класса.  
  
#### Для замены параметров шаблона  
  
1.  Добавьте следующий код в файле SimpleProjectNode.cs `using` инструкции.  
  
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
  
 Операторы присваивания определить разумные значения для пространства имен и новое имя класса. Два `ProjectNode.FileTemplateProcessor.AddReplace` вызовы метода замените значения соответствующего параметра шаблона с помощью этих новых значений.  
  
## Тестирование замена параметров шаблона  
 Теперь можно протестировать подстановку параметров шаблона.  
  
#### Чтобы проверить замена параметров шаблона  
  
1.  Начните отладку, а в экспериментальном экземпляре создайте новый SimpleProject.  
  
2.  Выполнение останавливается в точке останова в `AddFileFromTemplate` метод.  
  
3.  Проверьте значения `nameSpace` и `className` параметров.  
  
    -   `nameSpace` Получает значение элемента \< RootNamespace \> в файле шаблона проекта \\Templates\\Projects\\SimpleProject\\SimpleProject.myproj. В этом случае значение — «MyRootNamespace».  
  
    -   `className` Получает значение из класса имя исходного файла, без расширения имени файла. В этом случае первый файл для копирования в папку назначения является AssemblyInfo.cs; Таким образом значение className — «AssemblyInfo».  
  
4.  Удалите точку останова и нажмите клавишу F5, чтобы продолжить выполнение.  
  
     Visual Studio необходимо завершить создание проекта.  
  
5.  Откройте файл Program.cs в редакторе кода. Вы должны увидеть исходный код, подобный приведенному ниже.  
  
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
  
     Обратите внимание, что пространство имен теперь «MyRootNamespace» и «Программа» теперь имеет имя класса.  
  
6.  Начните отладку проекта. Новый проект должен компиляции, запуска и отображение «Hello VSX\!\!\!» в окне консоли.  
  
     ![Команда Simple Project](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 Поздравляем\! Вы реализовали систему базового управляемого проекта.