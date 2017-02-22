---
title: "Создание базового проекта системы, часть 2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Создание базового проекта системы, часть 2
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Первого пошагового руководства в данной серии [Создание базового проекта системы, часть 1](../extensibility/creating-a-basic-project-system-part-1.md), показано, как создать проект базовой системы. В этом пошаговом руководстве основан на основной проект системы путем добавления шаблона Visual Studio, страницу свойств и другие функции. Перед началом этого первого пошагового руководства необходимо выполнить.  
  
 В этом пошаговом руководстве объясняется, как создать тип проекта, который имеет .myproj расширение имени файла проекта. Для выполнения данного пошагового руководства, не нужно создать собственный язык, поскольку пошагового руководства занимает в существующей системе проектов Visual C\#.  
  
 В этом пошаговом руководстве объясняется, как выполнять эти задачи:  
  
-   Создание шаблона Visual Studio.  
  
-   Развертывание шаблона Visual Studio.  
  
-   Создать дочерний узел типа проекта в **Новый проект** диалоговое окно.  
  
-   Включите подстановку параметров в шаблоне Visual Studio.  
  
-   Создание страницы свойств проекта.  
  
> [!NOTE]
>  В этом пошаговом руководстве, основаны на проект C\#. Тем не менее за исключением особенностей, например расширения имен файлов, а также код, можно использовать те же действия для проекта Visual Basic.  
  
## Создание шаблона Visual Studio  
 [Создание базового проекта системы, часть 1](../extensibility/creating-a-basic-project-system-part-1.md) показано, как создать базовый шаблон и добавить его к системе проектов. Также показано, как зарегистрировать этот шаблон в Visual Studio с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут, который записывает полный путь к папке \\Templates\\Projects\\SimpleProject\\ в системном реестре.  
  
 С помощью шаблона Visual Studio \(VSTEMPLATE\-файл\) вместо базового проекта шаблона, можно управлять как шаблон появится в **Новый проект** диалоговое окно и заменяются как параметров шаблона.  VSTEMPLATE\-файл является XML\-файл, описывающий, как исходные файлы должны быть включены при создании проекта с помощью шаблона проекта системы. Сама система проектов, созданные сбор VSTEMPLATE\-файла и исходных файлов в ZIP\-файл и разворачивать путем копирования ZIP\-файл в расположение, известно, что Visual Studio. Этот процесс описан более подробно далее в этом пошаговом руководстве.  
  
1.  В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], откройте решение SimpleProject, которое вы создали, следуя [Создание базового проекта системы, часть 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2.  В файле SimpleProjectPackage.cs Найдите атрибут ProvideProjectFactory. Замените второй параметр \(имя проекта\) null, а четвертый параметр \(путь к папке шаблонов проекта\) с «.\\\\NullPath», как показано ниже.  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null, "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj", ".\\NullPath", LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  Добавьте файл XML с именем SimpleProject.vstemplate в папку \\Templates\\Projects\\SimpleProject\\.  
  
4.  Замените содержимое SimpleProject.vstemplate следующий код.  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"> <TemplateData> <Name>SimpleProject Application</Name> <Description> A project for creating a SimpleProject application </Description> <Icon>SimpleProject.ico</Icon> <ProjectType>SimpleProject</ProjectType> </TemplateData> <TemplateContent> <Project File="SimpleProject.myproj" ReplaceParameters="true"> <ProjectItem ReplaceParameters="true" OpenInEditor="true"> Program.cs </ProjectItem> <ProjectItem ReplaceParameters="true" OpenInEditor="false"> AssemblyInfo.cs </ProjectItem> </Project> </TemplateContent> </VSTemplate>  
    ```  
  
5.  В **Свойства** окно, выберите все пять файлов в папке \\Templates\\Projects\\SimpleProject\\ и набор **Действие при построении** для **ZipProject**.  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 В разделе \< TemplateData \> определяет расположение и внешний вид типа проекта SimpleProject в **Новый проект** диалоговом следующим образом:  
  
-   Элемент \< имя \> имя шаблона проекта приложения SimpleProject.  
  
-   Элемент \< Description \> содержит описание, которое отображается в **Новый проект** диалоговое окно при выборе шаблона проекта.  
  
-   Элемент \< Icon \> задает значок, который отображается вместе с типом проекта SimpleProject.  
  
-   Элемент \< ProjectType \> имена типа проекта в **Новый проект** диалоговое окно. Это имя заменяет имя параметра атрибута ProvideProjectFactory проекта.  
  
    > [!NOTE]
    >  Элемент \< ProjectType \> должен соответствовать `LanguageVsTemplate` аргумент `ProvideProjectFactory` атрибут в файле SimpleProjectPackage.cs.  
  
 В разделе \< TemplateContent \> описаны эти файлы, которые создаются при создании нового проекта:  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   Файл AssemblyInfo.cs  
  
 Все три файла имеют `ReplaceParameters` значение true, что позволяет подстановку параметров.  В файле Program.cs `OpenInEditor` присвоено значение true, вследствие чего файл необходимо открыть в редакторе кода, при создании проекта.  
  
 Дополнительные сведения об элементах в схеме шаблонов Visual Studio см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Если проект содержит несколько шаблонов Visual Studio, каждый шаблон находится в отдельной папке. Каждый файл в этой папке должен иметь **Действие при построении** значение **ZipProject**.  
  
## Добавление файла .vsct минимальный  
 Необходимо запустить Visual Studio в режиме распознавать новые или измененные шаблоны Visual Studio. Режим установки требуется файл .vsct должен присутствовать. Таким образом необходимо добавить файл .vsct минимальный в проект.  
  
1.  Добавьте файл XML с именем SimpleProject.vsct SimpleProject проект.  
  
2.  Замените содержимое файла SimpleProject.vsct с помощью следующего кода.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"> </CommandTable>  
    ```  
  
3.  Задайте **Действие при построении** этого файла для **VSCTCompile**. Это можно сделать только в CSPROJ\-файл не в **Свойства** окна. Убедитесь, что **Действие при построении** этот файл устанавливается в **Нет** на этом этапе.  
  
    1.  Щелкните правой кнопкой мыши узел SimpleProject и нажмите кнопку **Изменить SimpleProject.csproj**.  
  
    2.  В файле .csproj найдите элемент SimpleProject.vsct.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Изменить действие при построении **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  файл проекта и закройте редактор.  
  
    5.  Сохранить SimpleProject узел, а затем в **обозревателе решений** щелкните **перезагрузить проект**.  
  
## Изучение действий построения шаблона Visual Studio  
 Система построения проекта VSPackage обычно запускает Visual Studio в режиме, при изменении VSTEMPLATE\-файл или перестраивается проект, содержащий VSTEMPLATE\-файл. Читатели могут проследить, установив уровень детализации MSBuild обычный или более поздней версии.  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  Разверните **проекты и решения** а затем выберите **Построение и запуск**.  
  
3.  Задайте **уровень детализации выходных данных построения проекта MSBuild** для **норм**. Нажмите кнопку **ОК**.  
  
4.  Перестройте проект SimpleProject.  
  
 Шаг построения, чтобы создать ZIP\-файл проекта должен выглядеть примерно так.  
  
```  
ZipProjects: 1>  Zipping ProjectTemplates 1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip... 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip". 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip". 1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip 1>ZipItems: 1>  Zipping ItemTemplates 1>  SimpleProject ->  
```  
  
## Развертывание шаблона Visual Studio  
 Шаблоны Visual Studio не содержат сведения о пути. Таким образом ZIP\-файл шаблона должны быть развернуты в расположение, известно, что Visual Studio. Расположение папки Шаблоны\_проекта обычно является **\< % LOCALAPPDATA % \> \\Microsoft\\VisualStudio\\14.0Exp\\ProjectTemplates**.  
  
 Чтобы развернуть проект фабрики, программа установки требуются привилегии администратора. Развертывание шаблонов в узле установки Visual Studio: **14.0\\Common7\\IDE\\ProjectTemplates ...\\Microsoft Visual Studio**.  
  
## Проверка шаблона Visual Studio  
 Тестирование проекта фабрики для просмотра ли он создает иерархию проекта с помощью шаблона Visual Studio.  
  
1.  Сброс экспериментального экземпляра Visual Studio SDK.  
  
     На [!INCLUDE[win7](../debugger/includes/win7_md.md)]: В меню Пуск найдите **Microsoft Visual Studio и средств Microsoft Visual Studio SDK или** папку, а затем выберите **Сброс Microsoft Visual Studio экспериментального экземпляра**.  
  
     В более поздних версиях Windows: на начальном экране, тип **Сброс Microsoft Visual Studio \< version \> экспериментальный экземпляр**.  
  
2.  Откроется окно командной строки. При появлении слова `Press any key to continue`, нажмите клавишу ВВОД. После закрытия окна, откройте Visual Studio.  
  
3.  Перестройте проект SimpleProject и начать отладку. Откроется экспериментальный экземпляр.  
  
4.  В экспериментальном экземпляре создайте проект SimpleProject. В **Новый проект** диалоговом **SimpleProject**.  
  
5.  Вы должны увидеть новый экземпляр SimpleProject.  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2\_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2\_MyProj")  
  
## Создание дочернего узла типа проекта  
 Можно добавить дочерний узел в узел типа проекта в **Новый проект** диалоговое окно.  Например для типа проекта SimpleProject, может иметь дочерние узлы для консольных приложений, окно приложения, веб\-приложений и т. д.  
  
 Дочерние узлы создаются путем изменения файла проекта и добавление дочерних элементов \< OutputSubPath \> элементы \< ZipProject \>. При копировании шаблона во время построения или развертывания каждый дочерний узел становится вложенную папку шаблонов проектов.  
  
 В этом разделе показано, как создать дочерний узел консоли для типа проекта SimpleProject.  
  
1.  Переименуйте папку \\Templates\\Projects\\SimpleProject\\ в \\Templates\\Projects\\ConsoleApp\\.  
  
2.  В **Свойства** окно, выберите все пять файлов в папке \\Templates\\Projects\\ConsoleApp\\ и убедитесь, что **Действие при построении** равен **ZipProject**.  
  
3.  В файле SimpleProject.vstemplate добавьте следующую строку в конце раздела \< TemplateData \> непосредственно перед закрывающим тегом.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Шаблон консольного приложения в дочерний узел консоли и в родительском узле SimpleProject, которая расположена на один уровень выше дочерний узел в результате.  
  
4.  Сохраните файл SimpleProject.vstemplate.  
  
5.  В файле .csproj добавьте каждый элемент ZipProject \< OutputSubPath \>. Выгрузить проект, что и раньше и в файле проекта.  
  
6.  Найдите элементы \< ZipProject \>. Для каждого элемента \< ZipProject \> добавьте элемент \< OutputSubPath \> и присвойте ему значение консоли. ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico"> <OutputSubPath>Console</OutputSubPath> </ZipProject>  
    ```  
  
7.  Добавьте \< PropertyGroup \> в файле проекта:  
  
    ```  
    <PropertyGroup> <VsTemplateLanguage>SimpleProject</VsTemplateLanguage> </PropertyGroup>  
    ```  
  
8.  Сохраните файл проекта и перезагрузить проект.  
  
## Тестирование дочерний узел типа проекта  
 Тестирование измененный файл проекта для просмотра ли **консоли** дочерний узел отображается в **Новый проект** диалоговое окно.  
  
1.  Запустите **Сброс Microsoft Visual Studio экспериментального экземпляра** средство.  
  
2.  Перестройте проект SimpleProject и начать отладку. Должен появиться в экспериментальном экземпляре  
  
3.  В **Новый проект** диалоговое окно, нажмите кнопку **SimpleProject** узла.**Консольное приложение** шаблон появится в **шаблоны** области.  
  
4.  Разверните **SimpleProject** узла.**Консоли** появится дочерний узел.**SimpleProject приложения** шаблон остается в **шаблоны** области.  
  
5.  . Щелкните **Отменить** и остановить отладку  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2\_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2\_Subfolder")  
  
## Замена параметров шаблона проекта  
 [Создание базового проекта системы, часть 1](../extensibility/creating-a-basic-project-system-part-1.md) было показано, как перезаписать `ProjectNode.AddFileFromTemplate` метод для выполнения основных вида подстановку параметров шаблона. В этом разделе объясняется, как использовать более сложные параметры шаблона Visual Studio.  
  
 При создании проекта с помощью шаблона Visual Studio в **Новый проект** диалоговом параметры заменяются шаблон строки для настройки проекта. Параметр шаблона — это специальный маркер, который начинается и заканчивается знаком доллара, например, $time$. Следующие два параметра особенно полезны для включения настройки проектов, основанных на шаблоне:  
  
-   $GUID \[1\-10\] $ заменяется на новый идентификатор Guid. Можно указать до 10 уникальных идентификаторов GUID, например, $ $guid1.  
  
-   $safeprojectname$ является имя, указанное пользователем в **Новый проект** диалоговом удалены все небезопасные символы и пробелы.  
  
 Полный список параметров шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).  Если вы хотите создать собственный пользовательский шаблон параметр, см. раздел [NIB: как: передачи пользовательских параметров в шаблоны](http://msdn.microsoft.com/ru-ru/5bc2ad11-84c7-4683-a276-e5e00d85d8fb).  
  
#### Для замены параметров шаблона проекта  
  
1.  В файле SimpleProjectNode.cs удаление `AddFileFromTemplate` метод.  
  
2.  В файле \\Templates\\Projects\\ConsoleApp\\SimpleProject.myproj найдите свойство \< RootNamespace \> и измените его значение на $safeprojectname$.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  В файле \\Templates\\Projects\\SimpleProject\\Program.cs замените содержимое файла следующим кодом:  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace $safeprojectname$ { [Guid("$guid1$")] public class $safeprojectname$ { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
4.  Перестройте проект SimpleProject и начать отладку. Экспериментальный экземпляр должен отображаться.  
  
5.  Создайте новое приложение консоли SimpleProject. \(В **типы проектов** выберите **SimpleProject**. В разделе **Установленные шаблоны Visual Studio**, выберите **Консольное приложение**.\)  
  
6.  В только что созданный проект откройте файл Program.cs. Он должен выглядеть примерно следующим образом \(значения GUID в файле будут отличаться.\):  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace Console_Application1 { [Guid("00000000-0000-0000-00000000-00000000)"] public class Console_Application1 { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
## Создание страницы свойств проекта  
 Можно создать страницу свойств для данного типа проекта, чтобы пользователи могут просматривать и изменять свойства в проектах, основанных на шаблоне. В этом разделе показано, как создать страницу свойств зависят от конфигурации. Эту страницу основных свойств использует свойства сетки для отображения открытые свойства, которые предоставляют в классе страницы свойств.  
  
 Сформируйте класс страницы свойств из `SettingsPage` базового класса. Сетки свойств, предоставляемых `SettingsPage` класс поддерживает большинство примитивных типов данных и знает способ их отображения.  Кроме того `SettingsPage` класс знает, как для сохранения значений свойств в файле проекта.  
  
 Страницы свойств, созданные в этом разделе можно изменить и сохранить эти свойства проекта:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1.  Добавьте в файл SimpleProjectPackage.cs, это `ProvideObject` атрибут `SimpleProjectPackage` класса:  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))] public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     Эта строка регистрирует класс страницы свойств `GeneralPropertyPage` с COM.  
  
2.  Добавьте в файл SimpleProjectNode.cs, эти два переопределенного метода `SimpleProjectNode` класса:  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; } protected override Guid[] GetPriorityProjectDesignerPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; }  
    ```  
  
     Оба метода возвращают массив идентификаторов GUID на странице свойств.  Идентификатор GUID GeneralPropertyPage является единственным элементом в массиве, поэтому **страницы свойств** диалоговое окно отображается только на одной странице.  
  
3.  Добавьте файл класса с именем GeneralPropertyPage.cs SimpleProject проект.  
  
4.  Замените содержимое этого файла, используя следующий код:  
  
    ```  
    using System; using System.Runtime.InteropServices; using Microsoft.VisualStudio; using Microsoft.VisualStudio.Project; using System.ComponentModel; namespace SimpleProject { [ComVisible(true)] [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")] public class GeneralPropertyPage : SettingsPage { private string assemblyName; private OutputType outputType; private string defaultNamespace; public GeneralPropertyPage() { this.Name = "General"; } [Category("AssemblyName")] [DisplayName("AssemblyName")] [Description("The output file holding assembly metadata.")] public string AssemblyName { get { return this.assemblyName; } } [Category("Application")] [DisplayName("OutputType")] [Description("The type of application to build.")] public OutputType OutputType { get { return this.outputType; } set { this.outputType = value; this.IsDirty = true; } } [Category("Application")] [DisplayName("DefaultNamespace")] [Description("Specifies the default namespace for added items.")] public string DefaultNamespace { get { return this.defaultNamespace; } set { this.defaultNamespace = value; this.IsDirty = true; } } protected override void BindProperties() { this.assemblyName = this.ProjectMgr.GetProjectProperty( "AssemblyName", true); this.defaultNamespace = this.ProjectMgr.GetProjectProperty( "RootNamespace", false); string outputType = this.ProjectMgr.GetProjectProperty( "OutputType", false); this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType); } protected override int ApplyChanges() { this.ProjectMgr.SetProjectProperty( "AssemblyName", this.assemblyName); this.ProjectMgr.SetProjectProperty( "OutputType", this.outputType.ToString()); this.ProjectMgr.SetProjectProperty( "RootNamespace", this.defaultNamespace); this.IsDirty = false; return VSConstants.S_OK; } } }  
    ```  
  
     `GeneralPropertyPage` Класс предоставляет три открытых свойства AssemblyName, OutputType и RootNamespace. Поскольку AssemblyName отсутствует метод set, он отображается как свойство только для чтения. OutputType является Перечислимая константа, поэтому он представляется в виде раскрывающегося списка.  
  
     `SettingsPage` Предоставляет базовый класс `ProjectMgr` для сохранения свойств.`BindProperties` Использует метод `ProjectMgr` для получения значений свойств persisted и устанавливает соответствующие свойства.`ApplyChanges` Использует метод `ProjectMgr` для получения значений свойств и сохранить их в файл проекта. Устанавливает свойство `IsDirty` в значение true, чтобы означать, что для сохранения значения свойства.  Сохранение происходит при сохранении проекта или решения.  
  
5.  Перестройте решение SimpleProject и начать отладку. Экспериментальный экземпляр должен отображаться.  
  
6.  В экспериментальном экземпляре создайте новое приложение SimpleProject.  
  
7.  Visual Studio вызывает проекта фабрику для создания проекта с помощью шаблона Visual Studio. В редакторе кода открывается новый файл Program.cs.  
  
8.  Щелкните правой кнопкой мыши узел проекта в **обозревателе решений**, а затем нажмите кнопку **Свойства**.**Страницы свойств** диалоговое окно.  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2\_PropPage")  
  
## Тестирование страницы свойств проекта  
 Теперь вы можете протестировать можно изменить и изменить значения свойств.  
  
1.  В **страницы свойств MyConsoleApplication** диалоговом изменение **DefaultNamespace** для **MyApplication**.  
  
2.  Выберите **OutputType** а затем выберите **библиотеки классов**.  
  
3.  Щелкните **Применить**, а затем нажмите кнопку **ОК**.  
  
4.  Снова откройте **страницы свойств** диалогового окна и убедитесь, что изменения были сохранены.  
  
5.  Закройте экспериментальный экземпляр Visual Studio.  
  
6.  Откройте в экспериментальном экземпляре.  
  
7.  Снова откройте **страницы свойств** диалогового окна и убедитесь, что изменения были сохранены.  
  
8.  Закройте экспериментальный экземпляр Visual Studio.  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2\_PropPage2")