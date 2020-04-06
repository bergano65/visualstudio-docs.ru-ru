---
title: Создание базовой системы проекта, часть 2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739708"
---
# <a name="create-a-basic-project-system-part-2"></a>Создание базовой проектной системы, часть 2
Первое пошаговое из этой серии, [Создание базовой системы проекта, часть 1](../extensibility/creating-a-basic-project-system-part-1.md), показывает, как создать основную систему проекта. Это пошаговое решение основывается на базовой системе проекта, добавляя шаблон Visual Studio, страницу свойств и другие функции. Вы должны завершить первое пошаговое походе, прежде чем начать этот.

Это пошаговое решение учит, как создать тип проекта, который имеет расширение названия файла проекта *.myproj.* Чтобы завершить пошаговое решение, вам не нужно создавать свой собственный язык, потому что пошаговое решение заимствовано из существующей системы проекта Visual C.

Это пошаговое промывое учит, как выполнить эти задачи:

- Создайте шаблон Visual Studio.

- Развертывание шаблона Visual Studio.

- Создайте детский узлы типа проекта в диалоговом окне **нового проекта.**

- Включить замену параметров в шаблоне Visual Studio.

- Создайте страницу свойств проекта.

> [!NOTE]
> Шаги в этом пошаговом шаге основаны на проекте C-е. Однако, за исключением конкретики, такой как расширение и код имени файла, можно использовать те же шаги для проекта Visual Basic.

## <a name="create-a-visual-studio-template"></a>Создание шаблона Visual Studio
- [Создайте базовую проектную систему, в части 1 показано,](../extensibility/creating-a-basic-project-system-part-1.md) как создать базовый шаблон проекта и добавить его в проектную систему. Он также показывает, как зарегистрировать этот шаблон <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> с Visual Studio с помощью атрибута, который пишет полный путь * \\шаблонов »Проекты »SimpleProject\\ * папку в реестре системы.

Используя шаблон Visual Studio (файл *.vstemplate)* вместо базового шаблона проекта, вы можете контролировать, как шаблон отображается в диалоговом окне **нового проекта** и как заменяются параметры шаблона. Файл *.vstemplate* — это файл XML, описывающий, как исходные файлы должны быть включены при создании проекта с помощью шаблона проектной системы. Сама проектная система построена путем сбора файла *.vstemplate* и исходных файлов в файле *.zip* и развернута путем копирования файла *.zip* в место, известное Visual Studio. Этот процесс объясняется более подробно позже в этом пошаговом пошаговом пошаге.

1. В, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]открыть решение SimpleProject, которое вы создали, следуя [Создать основную систему проекта, часть 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. В *SimpleProjectPackage.cs* файле найдите атрибут ProvideProjectFactory. Замените второй параметр (название проекта) нулевым, а четвертый параметр (путь к папке шаблона проекта) на ". \\«NullPath», следующим образом.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Добавьте файл XML под названием *SimpleProject.vstemplate* в * \\папку «Шаблоны»-SimpleProject.\\ *

4. Замените содержимое *SimpleProject.vstemplate* следующим кодом.

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

5. В окне **Свойств** выберите все пять файлов в папке * \\«Шаблоны»Проекты и SimpleProject\\ * и установите действие на **сборку** в **qipProject.**

    ![Простой проект Фолдер](../extensibility/media/simpproj2.png "SimpProj2")

    Раздел \<TemplateData> определяет местоположение и внешний вид типа проекта SimpleProject в диалоговом окне **нового проекта** следующим образом:

- Элемент \<Name> называет шаблон проекта приложением SimpleProject.

- Элемент \<«Описание>» содержит описание, которое отображается в диалоговом окне **нового проекта** при выборе шаблона проекта.

- Элемент \<> значок определяет значок, который появляется вместе с типом проекта SimpleProject.

- Элемент \<ProjectType> назван типом проекта в диалоговом окне **нового проекта.** Это имя заменяет параметр названия проекта атрибута ProvideProjectFactory.

  > [!NOTE]
  > Элемент \<ProjectType> должен `LanguageVsTemplate` соответствовать `ProvideProjectFactory` аргументу атрибута в файле SimpleProjectPackage.cs.

  Раздел \<> TemplateContent описывает эти файлы, которые генерируются при создании нового проекта:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Все три `ReplaceParameters` файла настроены на истину, что позволяет заменить параметры. *Файл Program.cs* `OpenInEditor` установлен на истину, что приводит к открытию файла в редакторе кода при создании проекта.

  Для получения дополнительной информации об элементах в схеме шаблона Visual Studio см. [Visual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)

> [!NOTE]
> Если в проекте имеется несколько шаблонов Visual Studio, каждый шаблон находится в отдельной папке. Каждый файл в этой папке должен иметь набор **действий по сборке** для **qipProject.**

## <a name="adding-a-minimal-vsct-file"></a>Добавление минимального файла .vsct
 Visual Studio должна быть запущена в режиме настройки, чтобы распознать новый или измененный шаблон Visual Studio. Режим настройки требует присутствия файла *.vsct.* Поэтому необходимо добавить в проект минимальный файл *.vsct.*

1. Добавьте в проект SimpleProject файл XML под названием *SimpleProject.vsct.*

2. Замените содержимое файла *SimpleProject.vsct* следующим кодом.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Установите **действие сборки** этого файла на **VSCTCompile.** Это можно сделать только в файле *.csproj,* а не в окне **свойств.** Убедитесь, что на данный момент **действие Build Action** этого файла не установлено ни на **один.**

    1. Нажмите правой кнопкой кнопку узла SimpleProject, а затем нажмите **Edit SimpleProject.csproj**.

    2. В файле *.csproj* найдите элемент *SimpleProject.vsct.*

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Измените действие сборки на **VSCTCompile.**

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. файл проекта и закройте редактор.

    5. Сохранить узло SimpleProject, а затем в проекте **Reload Project** **Solution Explorer.**

## <a name="examine-the-visual-studio-template-build-steps"></a>Изучите шаги построения шаблона Visual Studio
 Система сборки проектов VSPackage обычно запускает Visual Studio в режиме настройки при изменении файла *.vstemplate* или перестроен проект, содержащий файл *.vstemplate.* Вы можете следовать вместе, установив уровень многословности MSBuild к нормальному или выше.

1. В меню **Сервис** выберите команду **Параметры**.

2. Расширьте узлы **проектов и решений,** а затем выберите **«Сборка и запуск».**

3. Установите **проект MSBuild построить выход многословность** к **нормальному**. Нажмите кнопку **ОК**.

4. Перестроить проект SimpleProject.

    Шаг сборки для создания файла проекта *.zip* должен напоминать следующий пример.

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

## <a name="deploy-a-visual-studio-template"></a>Развертывание шаблона Visual Studio
Шаблоны Visual Studio не содержат информацию о путях. Таким образом, файл *шаблона .zip* должен быть развернут в место, известное Visual Studio. Местоположение папки ProjectTemplates, как правило, *<%LOCALAPPDATA%>»Microsoft-VisualStudio -14.0Exp-ProjectTemplates*.

Для развертывания фабрики проекта программа установки должна иметь привилегии администратора. Он развертывает шаблоны под узла установки Visual Studio: *...*

## <a name="test-a-visual-studio-template"></a>Тестшаблон Visual Studio
Проверьте свою фабрику проектов, чтобы увидеть, создает ли она иерархию проектов с помощью шаблона Visual Studio.

1. Перезагрузка экспериментального экземпляра Visual Studio SDK.

    На [!INCLUDE[win7](../debugger/includes/win7_md.md)]: В меню **«Пуск»** найдите папку **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools,** а затем выберите **сбросить экспериментальный экземпляр Microsoft Visual Studio.**

    На более поздних версиях Windows: На **начальном** экране введите **сбросить версию Microsoft Visual Studio \<> Experimental Instance.**

2. Отображается окно запроса команды. Когда вы видите слова **Нажмите любой ключ, чтобы продолжить,** нажмите **ENTER**. После закрытия окна откройте Visual Studio.

3. Перестроить проект SimpleProject и начать отладку. Появляется экспериментальный экземпляр.

4. В экспериментальном примере создайте проект SimpleProject. В диалоговом окне **нового проекта** выберите **SimpleProject**.

5. Вы должны увидеть новый экземпляр SimpleProject.

    ![Простой проект Новая инстанция](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Мой проект Новый экземпляр](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Создание детского узла типа проекта
В диалоговом поле **нового проекта** можно добавить узла детского узла в узло типа проекта. Например, для типа проекта SimpleProject можно иметь детские узлы для консольных приложений, оконных приложений, веб-приложений и так далее.

Детские узлы создаются путем изменения \<файла проекта и \<добавления OutputSubPath> элементов>. Когда шаблон скопирован во время сборки или развертывания, каждый узлы-изута становятся подфоном папки шаблонов проекта.

В этом разделе показано, как создать узлы для детского узла консоли для типа проекта SimpleProject.

1. Переименуй * \\папку «Шаблоны»Проекты и SimpleProject\\ * в * \\шаблоны(Проекты и ConsoleApp\\*.

2. В окне **Свойств** выберите все пять файлов в папке * \\«Шаблоны»-ConsoleApp\\ * и убедитесь, что **действие Build Action** настроено на **«ЗипПроект».**

3. В файле SimpleProject.vstemplate добавьте следующую строку в конце раздела \<TemplateData>, непосредственно перед закрытием тега.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Это приводит к тому, что шаблон консольного приложения отображается как в детском узло Console, так и в родительском узло SimpleProject, который на один уровень выше детского узла.

4. Сохранить файл *SimpleProject.vstemplate.*

5. В *файле .csproj* добавьте \<OutputSubPath> к каждому из элементов зиппроекта. Выгрузите проект, как и прежде, и отодевите файл проекта.

6. Найдите \<элементы>. К \<каждому элементу>, добавляйте элемент \<OutputSubPath> и придайте ему консоль значения. ЗипПроект

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

7. Добавьте \<эту> PropertyGroup в файл проекта:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Сохранить файл проекта и перезагрузить проект.

## <a name="test-the-project-type-child-node"></a>Протестировать детский узла типа проекта
Проверьте измененный файл проекта, чтобы узнать, отображается ли детский узло **Console** в диалоговом окне **нового проекта.**

1. Выполнить сбросить инструмент **экспериментальной инстанции Microsoft Visual Studio.**

2. Перестроить проект SimpleProject и начать отладку. Экспериментальный экземпляр должен появиться

3. В диалоге **нового проекта** щелкните узло **SimpleProject.** Шаблон **консольного приложения** должен отображаться в панели **шаблонов.**

4. Расширьте узла **SimpleProject.** Должен отображаться узла **консольного** ребенка. Шаблон **приложения SimpleProject** продолжает отображаться в панели **шаблонов.**

5. Нажмите **Отмена** и остановить отладку.

    ![Простой проект Rollup](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Простой узлы консоли проекта](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Заменить параметры шаблона проекта
- [Создание базовой проектной системы, часть 1 показала,](../extensibility/creating-a-basic-project-system-part-1.md) как перезаписать `ProjectNode.AddFileFromTemplate` метод, чтобы сделать базовый вид замены параметров шаблона. В этом разделе рассказывается о том, как использовать более сложные параметры шаблона Visual Studio.

При создании проекта с помощью шаблона Visual Studio в диалоговом окне **нового проекта** параметры шаблона заменяются строками для настройки проекта. Параметр шаблона — это специальный токен, который начинается и заканчивается знаком доллара, например, $time$. Следующие два параметра особенно полезны для настройки в проектах, основанных на шаблоне:

- $GUID заменяется новым Guid. Можно указать до 10 уникальных GUID, например, $guid1$.

- $safeprojectname $ — это имя, предоставленное пользователем в диалоговом окне **нового проекта,** измененное для удаления всех небезопасных символов и пробелов.

  Полный список параметров шаблона [см.](../ide/template-parameters.md)

### <a name="to-substitute-project-template-parameters"></a>Замена параметров шаблона проекта

1. В *SimpleProjectNode.cs* файле `AddFileFromTemplate` удалите метод.

2. В файле * \\Templates-Projects-ConsoleApp-SimpleProject.myproj* \<найдите свойство RootNamespace> и измените его стоимость до $safeprojectname $.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. В файле * \\Templates-Projects-SimpleProject.cs* замените содержимое файла следующим кодом:

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

4. Перестроить проект SimpleProject и начать отладку. Экспериментальный экземпляр должен появиться.

5. Создайте новое приложение SimpleProject Console. (В **панели типов проекта** выберите **SimpleProject**. Под **Visual Studio установлены шаблоны,** выберите **Консоль Ност.)**

6. В недавно созданном проекте, *открытые Program.cs*. Он должен выглядеть примерно следующим (значения GUID в файле будут отличаться.):

    ```csharp
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

## <a name="create-a-project-property-page"></a>Создание страницы свойств проекта
Можно создать страницу свойств для типа проекта, чтобы пользователи могли просматривать и изменять свойства в проектах, основанных на шаблоне. В этом разделе показано, как создать страницу свойств, не зависях от конфигурации. Эта базовая страница свойств использует сетку свойств для отображения общедоступных свойств, которые вы предоставляете в классе страницы свойств.

Извлеките класс страницы свойств из базового `SettingsPage` класса. Сетка `SettingsPage` свойств, предоставляемая классом, знает большинство примитивных типов данных и знает, как их отобразить. Кроме того, `SettingsPage` класс знает, как сохранить значения свойств в файле проекта.

Страница свойств, создаваемых в этом разделе, позволяет изменять и сохранять эти свойства проекта:

- AssemblyName

- OutputType

- RootNamespace.

1. В *файле SimpleProjectPackage.cs* `ProvideObject` добавьте `SimpleProjectPackage` этот атрибут в класс:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Это регистрирует класс `GeneralPropertyPage` страницы свойств с COM.

2. В *SimpleProjectNode.cs* файле добавьте эти два `SimpleProjectNode` переопределенных метода в класс:

    ```csharp
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

    Оба этих метода возвращают массив ГРАФИЧЕСКИх интерфейсов страницы свойств. GeneralPropertyPage GUID является единственным элементом в массиве, поэтому в диалоговом поле **Страницы свойств** будет отображаться только одна страница.

3. Добавьте файл класса под названием *GeneralPropertyPage.cs* в проект SimpleProject.

4. Замените содержимое этого файла с помощью следующего кода:

    ```csharp
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
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    Класс `GeneralPropertyPage` предоставляет три открытых свойства AssemblyName, OutputType и RootNamespace. Поскольку у AssemblyName нет установленного метода, он отображается как свойство только для чтения. OutputType — это перечисленный константа, поэтому он отображается как список выпадающих данных.

    Базовый `SettingsPage` класс `ProjectMgr` обеспечивает сохранение свойств. Метод `BindProperties` используется `ProjectMgr` для извлечения сохраняемых значений свойств и установки соответствующих свойств. Метод `ApplyChanges` использует `ProjectMgr` для получения значений свойств и сохранения их в файле проекта. The property set method sets `IsDirty` to true to indicate that the properties have to be persisted. Сохранение происходит при сохранении проекта или решения.

5. Перестроить решение SimpleProject и начать отладку. Экспериментальный экземпляр должен появиться.

6. В экспериментальном примере создайте новое приложение SimpleProject.

7. Visual Studio вызывает вашу фабрику проекта для того чтобы создать проект используя шаблон visual Studio. Новый *файл Program.cs* открыт в редакторе кода.

8. Нажмите правой кнопкой наузло узла проекта в **Solution Explorer,** а затем нажмите **Свойства**. Откроется диалоговое окно **Страницы свойств**.

    ![Страница свойства простого проекта](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Проверьте страницу свойства проекта
Теперь можно проверить, можно ли изменять и изменять значения свойств.

1. В диалоговом окне **страниц свойств MyConsoleApplication** измените **пространство по умолчанию** **на MyApplication.**

2. Выберите свойство **OutputType,** а затем выберите **библиотеку класса.**

3. Щелкните **Применить** и нажмите кнопку **ОК**.

4. Повторно откройте диалоговое окно **Страниц ы свойств** и убедитесь, что ваши изменения были упорны.

5. Закройте экспериментальный экземпляр Visual Studio.

6. Повторно откройте экспериментальный экземпляр.

7. Повторно откройте диалоговое окно **Страниц ы свойств** и убедитесь, что ваши изменения были упорны.

8. Закройте экспериментальный экземпляр Visual Studio.
    ![Закрыть экспериментальный экземпляр](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
