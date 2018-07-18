---
title: Создание базового проекта системы, часть 2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f39150f02481e18997035a8027518648fa410f48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107950"
---
# <a name="creating-a-basic-project-system-part-2"></a>Создание базового проекта системы, часть 2
В этой серии первого пошагового руководства [Создание базовой системы проектов, часть 1](../extensibility/creating-a-basic-project-system-part-1.md), показано, как создать базовый проект систему. В этом пошаговом руководстве построена в системе базовый проект шаблона Visual Studio, страницу свойств и другие функции. Перед началом этого первого пошагового руководства необходимо выполнить.  
  
 В этом пошаговом руководстве учебные материалы по созданию типа проекта, который содержит .myproj расширение имени файла проекта. Для выполнения данного пошагового руководства, у вас создать собственный язык, поскольку пошагового руководства занимает в существующей системе проектов Visual C#.  
  
 В этом пошаговом руководстве рассматриваются способы выполнения этих задач:  
  
-   Создание шаблона Visual Studio.  
  
-   Развертывание шаблона Visual Studio.  
  
-   Создать дочерний узел типа проекта в **новый проект** диалоговое окно.  
  
-   Включите подстановку параметров в шаблоне Visual Studio.  
  
-   Создание страницы свойств проекта.  
  
> [!NOTE]
>  Действия, описанные в этом пошаговом руководстве основаны на проекте C#. Тем не менее за исключением особенностей, например расширения имен файлов, а также код, можно использовать те же действия для проекта Visual Basic.  
  
## <a name="creating-a-visual-studio-template"></a>Создание шаблона Visual Studio  
 [Создание базовой системы проектов, часть 1](../extensibility/creating-a-basic-project-system-part-1.md) показано, как создать базовый проект шаблона и добавить его в систему проекта. Также показано, как зарегистрировать этот шаблон в Visual Studio с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут, который записывает полный путь к папке \Templates\Projects\SimpleProject\ в системном реестре.  
  
 С помощью шаблона Visual Studio (файл VSTEMPLATE) вместо базового проекта шаблона, можно управлять как шаблон появится в **новый проект** диалоговое окно и способ замены параметров шаблона.  VSTEMPLATE-файл является XML-файл, который описывает, как исходные файлы должны быть включены при создании проекта с помощью шаблона проекта системы. Сама система проекта построения, так как VSTEMPLATE-файл и исходные файлы в ZIP-файл и развертывания путем копирования ZIP-файл в расположение, известно, что Visual Studio. Этот процесс описан более подробно далее в этом пошаговом руководстве.  
  
1.  В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], откройте SimpleProject решение, которое вы создали [Создание базовой системы проектов, часть 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2.  Найдите в файле SimpleProjectPackage.cs ProvideProjectFactory атрибута. Замените второй параметр (имя проекта) со значением null, а четвертый параметр (путь к папке проекта шаблона)». \\\NullPath», как показано ниже.  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
        ".\\NullPath",  
    LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  Добавьте в XML-файл с именем SimpleProject.vstemplate в папку \Templates\Projects\SimpleProject\.  
  
4.  Замените содержимое SimpleProject.vstemplate следующий код.  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
      <TemplateData>  
        <Name>SimpleProject Application</Name>  
        <Description>  
            A project for creating a SimpleProject application  
         </Description>  
         <Icon>SimpleProject.ico</Icon>  
         <ProjectType>SimpleProject</ProjectType>  
      </TemplateData>  
      <TemplateContent>  
        <Project File="SimpleProject.myproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
              Program.cs  
          </ProjectItem>  
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
             AssemblyInfo.cs  
          </ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
5.  В **свойства** окно, выберите все пять файлов в папке \Templates\Projects\SimpleProject\ и набор **действие при построении** для **ZipProject**.  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 \<TemplateData > раздел определяет расположение и внешний вид тип проекта SimpleProject в **новый проект** диалоговом следующим образом:  
  
-   \<Имя > шаблон проекта приложения SimpleProject именах элементов.  
  
-   \<Описание > содержит описание, которое отображается в **новый проект** диалоговое окно при выборе шаблона проекта.  
  
-   \<Значок > элемент задает значок, который отображается вместе с SimpleProject типа проекта.  
  
-   \<ProjectType > тип проекта в именах элементов **новый проект** диалоговое окно. Это имя заменяет имя параметра атрибута ProvideProjectFactory проекта.  
  
    > [!NOTE]
    >  \<ProjectType > элемент должен соответствовать `LanguageVsTemplate` аргумент `ProvideProjectFactory` атрибут в файле SimpleProjectPackage.cs.  
  
 \<TemplateContent > разделе описываются эти файлы, которые создаются при создании нового проекта:  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   AssemblyInfo.cs  
  
 Все три файла имеют `ReplaceParameters` значение true, что позволяет подстановку параметров.  В файле Program.cs `OpenInEditor` присвоено значение true, что файл открыт в редакторе кода, при создании проекта.  
  
 Дополнительные сведения об элементах в схеме шаблона Visual Studio см. в разделе [Справочник схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Если проект включает несколько шаблонов Visual Studio, каждый шаблон находится в отдельной папке. Каждый файл в этой папке должен иметь **действие при построении** значение **ZipProject**.  
  
## <a name="adding-a-minimal-vsct-file"></a>Добавление минимальной vsct-файл  
 В режиме установки для распознавания нового или измененного шаблона Visual Studio необходимо запустить Visual Studio. Режим установки требует vsct-файл должен присутствовать. Таким образом необходимо добавить минимальный vsct-файл в проект.  
  
1.  Добавьте в XML-файл с именем SimpleProject.vsct SimpleProject проект.  
  
2.  Замените содержимое файла SimpleProject.vsct следующий код.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  Задать **действие при построении** для этого файла в **VSCTCompile**. Это можно сделать только в CSPROJ-файл не в **свойства** окна. Убедитесь, что **действие при построении** этот файл устанавливается в **нет** на этом этапе.  
  
    1.  Щелкните правой кнопкой мыши узел SimpleProject и нажмите кнопку **изменить SimpleProject.csproj**.  
  
    2.  Найдите элемент SimpleProject.vsct CSPROJ-файл.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Изменить действие при построении **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  файл проекта и закройте редактор.  
  
    5.  Сохранить SimpleProject узел, а затем в **обозревателе решений** щелкните **перезагрузить проект**.  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Изучение действий построения шаблона Visual Studio  
 При изменении VSTEMPLATE-файл или перестроить проект, содержащий VSTEMPLATE-файл в режиме системы построения проекта VSPackage обычно выполняется Visual Studio. Можно продолжить работу с установкой уровня детализации MSBuild обычный или более поздней версии.  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  Разверните **проекты и решения** узел, а затем выберите **построение и запуск**.  
  
3.  Задать **детализации, выходные данные построения проекта MSBuild** для **обычный**. Нажмите кнопку **ОК**.  
  
4.  Перестройте проект SimpleProject.  
  
 На этапе построения для создания ZIP-файл проекта должен выглядеть примерно так.  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploying-a-visual-studio-template"></a>Развертывание шаблона Visual Studio  
 Шаблоны Visual Studio не содержат сведения о пути. Таким образом ZIP-файле шаблона должны быть развернуты в расположение, известно, что Visual Studio. Расположение папки Шаблоны_проекта обычно является  **\<% LOCALAPPDATA % > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**.  
  
 Чтобы развернуть проект фабрики, программа установки требуются права администратора. Он развертывает шаблонов в узле установки Visual Studio: **14.0\Common7\IDE\ProjectTemplates ...\Microsoft Visual Studio**.  
  
## <a name="testing-a-visual-studio-template"></a>Проверка шаблона Visual Studio  
 Тестирование проекта фабрику, чтобы понять, каким он иерархии проекта с помощью шаблона Visual Studio.  
  
1.  Сброс экспериментального экземпляра Visual Studio SDK.  
  
     На [!INCLUDE[win7](../debugger/includes/win7_md.md)]: В меню «Пуск» найдите **Microsoft Visual Studio и средств Microsoft Visual Studio SDK и** папки, а затем выберите **сбросить Microsoft Visual Studio экспериментальный экземпляр**.  
  
     В более поздних версиях Windows: на начальном экране, введите **Сброс Microsoft Visual Studio \<версии > экспериментальный экземпляр**.  
  
2.  Откроется окно командной строки. При появлении слова `Press any key to continue`, нажмите клавишу ВВОД. После закрытия окна, откройте Visual Studio.  
  
3.  Перестройте проект SimpleProject и начните отладку. Откроется экспериментальный экземпляр.  
  
4.  В экспериментальном экземпляре создайте проект SimpleProject. В **новый проект** выберите **SimpleProject**.  
  
5.  Вы увидите новый экземпляр SimpleProject.  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>Создание дочерний узел типа проекта  
 Добавляемый дочерний узел узел типа проекта в **новый проект** диалоговое окно.  Например для типа проекта SimpleProject, может иметь дочерние узлы для консольных приложений, окно приложения, веб-приложений и т. д.  
  
 Дочерние узлы создаются путем изменения файла проекта и добавление \<OutputSubPath > дочерние элементы \<ZipProject > элементов. При копировании шаблона во время сборки или развертывания, каждый дочерний узел становится вложенную папку шаблонов проектов.  
  
 В этом разделе показано, как создать дочерний узел типа проекта SimpleProject консоли.  
  
1.  Задайте для папки \Templates\Projects\SimpleProject\ \Templates\Projects\ConsoleApp\\.  
  
2.  В **свойства** выберите все пять файлов в папке \Templates\Projects\ConsoleApp\ и убедитесь, что **действие при построении** равно **ZipProject**.  
  
3.  В файле SimpleProject.vstemplate добавьте следующую строку в конце \<TemplateData > раздел непосредственно перед закрывающим тегом.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     В этом случае шаблон консольного приложения для отображения в консоли дочернем узле и в родительском узле SimpleProject, находящемся на один уровень выше дочернего узла.  
  
4.  Сохраните файл SimpleProject.vstemplate.  
  
5.  Добавьте в файл .csproj \<OutputSubPath > для каждого из элементов ZipProject. Выгрузить проект, как и прежде и в файле проекта.  
  
6.  Найдите \<ZipProject > элементов. Каждому \<ZipProject > элемента, добавьте \<OutputSubPath > элемент и присвойте ему значение консоли. ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7.  Добавьте это \<PropertyGroup > в файл проекта:  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  Сохраните файл проекта и перезагрузить проект.  
  
## <a name="testing-the-project-type-child-node"></a>Тестирование дочерний узел типа проекта  
 Проверить файл измененный проект, чтобы увидеть ли **консоли** дочерний узел отображается в **новый проект** диалоговое окно.  
  
1.  Запустите **Сброс Microsoft Visual Studio экспериментальный экземпляр** средства.  
  
2.  Перестройте проект SimpleProject и начните отладку. Откроется экспериментальный экземпляр  
  
3.  В **новый проект** диалоговое окно, нажмите кнопку **SimpleProject** узла. **Консольное приложение** шаблон появится в **шаблоны** области.  
  
4.  Разверните **SimpleProject** узла. **Консоли** должен отображаться дочерний узел. **Приложения SimpleProject** шаблон будет отображаться в **шаблоны** области.  
  
5.  . Нажмите кнопку **отменить** и остановить отладку  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>Замена параметров шаблона проекта  
 [Создание базовой системы проектов, часть 1](../extensibility/creating-a-basic-project-system-part-1.md) было показано, как перезаписать `ProjectNode.AddFileFromTemplate` метод для выполнения основной тип замена параметров шаблона. В этом разделе объясняется, как использовать более сложные параметры шаблона Visual Studio.  
  
 При создании проекта с помощью шаблона Visual Studio в **новый проект** диалоговое окно, заменяются параметрами шаблон строки для настройки проекта. Параметр шаблона — это специальный маркер, который начинается и заканчивается знаком доллара, например, $time$. Следующие два параметра особенно полезны для включения настройки в проектах, основанных на шаблоне:  
  
-   $ $GUID [1-10] заменяется на новый идентификатор Guid. Можно указать до 10 уникальных идентификаторов GUID, например, $ $guid1.  
  
-   $safeprojectname$ — это имя, предоставленное пользователем в **новый проект** диалоговое окно, изменить, чтобы удалить все небезопасные символы и пробелы.  
  
 Полный список параметров шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).  
  
#### <a name="to-substitute-project-template-parameters"></a>Для замены параметров шаблона проекта  
  
1.  В файле SimpleProjectNode.cs удалить `AddFileFromTemplate` метод.  
  
2.  Найдите в файле \Templates\Projects\ConsoleApp\SimpleProject.myproj \<RootNamespace > свойства и измените его значение на $safeprojectname$.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  В файле \Templates\Projects\SimpleProject\Program.cs замените содержимое файла следующим кодом:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4.  Перестройте проект SimpleProject и начните отладку. Откроется экспериментальный экземпляр.  
  
5.  Создайте новый SimpleProject консольное приложение. (В **типов проектов** выберите **SimpleProject**. В разделе **установленные шаблоны Visual Studio**выберите **консольное приложение**.)  
  
6.  В только что созданный проект откройте файл Program.cs. Он должен выглядеть примерно следующим образом (значения GUID в файле будут отличаться.):  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creating-a-project-property-page"></a>Создание страницы свойств проекта  
 Можно создать страницу свойств для данного типа проекта, чтобы пользователи могут просматривать и изменять свойства в проектах, основанных на шаблоне. В этом разделе показано, как создать страницу свойств зависят от конфигурации. Эту страницу основных свойств использует сетку свойств для отображения открытых свойств, предоставляемых в вашего класса страницы свойств.  
  
 Является производным класса страницы свойств из `SettingsPage` базового класса. Сетки свойств, предоставляемых `SettingsPage` класса поддерживают большинство примитивных типов данных и знает, как их отображения.  Кроме того `SettingsPage` класс знает, как сохранить значения свойств в файл проекта.  
  
 Страницы свойств, созданные в этом разделе можно изменить и сохранить эти свойства проекта:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1.  В файле SimpleProjectPackage.cs добавьте это `ProvideObject` атрибут `SimpleProjectPackage` класса:  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))]  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     Эта строка регистрирует класса страницы свойств `GeneralPropertyPage` в COM.  
  
2.  В файле SimpleProjectNode.cs добавьте эти два переопределенного метода `SimpleProjectNode` класса:  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
    }  
    protected override Guid[] GetPriorityProjectDesignerPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
         return result;  
    }  
    ```  
  
     Оба эти метода возвращать массив идентификаторов GUID на странице свойств.  Идентификатор GUID GeneralPropertyPage является единственным элементом в массиве, поэтому **страницы свойств** диалоговое окно отображается только на одной странице.  
  
3.  Добавьте файл класса с именем GeneralPropertyPage.cs SimpleProject проект.  
  
4.  Замените содержимое этого файла, используя следующий код:  
  
    ```  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Project;  
    using System.ComponentModel;  
  
    namespace SimpleProject  
    {  
        [ComVisible(true)]  
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
        public class GeneralPropertyPage : SettingsPage  
        {  
            private string assemblyName;  
            private OutputType outputType;  
            private string defaultNamespace;  
  
            public GeneralPropertyPage()  
            {  
                this.Name = "General";  
            }  
  
            [Category("AssemblyName")]  
            [DisplayName("AssemblyName")]  
            [Description("The output file holding assembly metadata.")]  
            public string AssemblyName  
            {  
                get { return this.assemblyName; }  
            }  
            [Category("Application")]  
            [DisplayName("OutputType")]  
            [Description("The type of application to build.")]  
            public OutputType OutputType  
            {  
                get { return this.outputType; }  
                set { this.outputType = value; this.IsDirty = true; }  
            }  
            [Category("Application")]  
            [DisplayName("DefaultNamespace")]  
            [Description("Specifies the default namespace for added items.")]  
            public string DefaultNamespace  
            {  
                get { return this.defaultNamespace; }  
                set { this.defaultNamespace = value; this.IsDirty = true; }  
            }  
  
            protected override void BindProperties()  
            {  
                this.assemblyName = this.ProjectMgr.GetProjectProperty(  
    "AssemblyName", true);  
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
    "RootNamespace", false);  
  
                string outputType = this.ProjectMgr.GetProjectProperty(  
    "OutputType", false);  
                this.outputType =   
    (OutputType)Enum.Parse(typeof(OutputType), outputType);  
            }  
  
            protected override int ApplyChanges()  
            {  
                this.ProjectMgr.SetProjectProperty(  
    "AssemblyName", this.assemblyName);  
                this.ProjectMgr.SetProjectProperty(  
    "OutputType", this.outputType.ToString());  
                this.ProjectMgr.SetProjectProperty(  
    "RootNamespace", this.defaultNamespace);  
                this.IsDirty = false;  
  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    ```  
  
     `GeneralPropertyPage` Класс предоставляет три открытых свойства AssemblyName OutputType и RootNamespace. Так как AssemblyName отсутствует метод set, он отображается как доступное только для чтения. OutputType является константа перечислимого типа, поэтому он отображается как раскрывающийся список.  
  
     `SettingsPage` Базовый класс предоставляет `ProjectMgr` для сохранения свойств. `BindProperties` Использует метод `ProjectMgr` для получения значений свойств persisted и задания соответствующих свойств.  `ApplyChanges` Использует метод `ProjectMgr` для получения значений свойств и сохраняет их в файл проекта. Свойство метода задает `IsDirty` в значение true указывает, что свойства имеют должны сохраняться.  Сохраняемости происходит при сохранении проекта или решения.  
  
5.  Перестроить решение SimpleProject и начните отладку. Откроется экспериментальный экземпляр.  
  
6.  В экспериментальном экземпляре создайте новое приложение SimpleProject.  
  
7.  Visual Studio вызывает проекта фабрику для создания проекта с помощью шаблона Visual Studio. В редакторе кода открывается новый файл Program.cs.  
  
8.  Щелкните правой кнопкой мыши узел проекта в **обозревателе решений**, а затем нажмите кнопку **свойства**. Откроется диалоговое окно **Страницы свойств**.  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>Тестирование на странице свойств проекта  
 Теперь можно проверить, можно изменить, а также изменения значений свойства.  
  
1.  В **страницы свойств MyConsoleApplication** диалоговом изменение **DefaultNamespace** для **MyApplication**.  
  
2.  Выберите **OutputType** свойства, а затем выберите **библиотеки классов**.  
  
3.  Нажмите кнопку **применить**, а затем нажмите кнопку **ОК**.  
  
4.  Снова откройте **страницы свойств** диалоговое окно и проверить, что изменения были сохранены.  
  
5.  Закройте экспериментальный экземпляр Visual Studio.  
  
6.  Снова откройте экспериментальный экземпляр.  
  
7.  Снова откройте **страницы свойств** диалоговое окно и проверить, что изменения были сохранены.  
  
8.  Закройте экспериментальный экземпляр Visual Studio.  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")