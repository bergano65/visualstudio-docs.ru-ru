---
title: Создание системы базового проекта, часть 2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d23c0803bb81b34156d2cdb56e54388ba3cc5661
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681313"
---
# <a name="create-a-basic-project-system-part-2"></a>Создание системы базового проекта, часть 2
Первого пошагового руководства в этой серии [Создание системы базового проекта, часть 1](../extensibility/creating-a-basic-project-system-part-1.md), демонстрируется создание системы базового проекта. В этом пошаговом руководстве развития системы базового проекта шаблона Visual Studio, страницу свойств и другие функции. Прежде чем начать, необходимо выполнить первого пошагового руководства.

В этом пошаговом руководстве объясняется, как создать тип проекта, который имеет расширение имени файла проекта *.myproj*. Для выполнения данного пошагового руководства, у вас нет для создания собственного языка, поскольку заимствует пошагового руководства в существующей системе проектов Visual C#.

В этом пошаговом руководстве объясняется, как выполнять эти задачи:

- Создание шаблона Visual Studio.

- Развертывание шаблона Visual Studio.

- Создать дочерний узел типа проекта в **новый проект** диалоговое окно.

- Включение подстановки параметров в шаблоне Visual Studio.

- Создание страницы свойств проекта.

> [!NOTE]
> Действия, описанные в этом пошаговом руководстве основаны на проекте C#. Тем не менее за исключением особенностей, таких как расширения имен файлов и кода, можно использовать те же действия для проекта Visual Basic.

## <a name="create-a-visual-studio-template"></a>Создание шаблона Visual Studio
- [Создание системы базового проекта, часть 1](../extensibility/creating-a-basic-project-system-part-1.md) показано, как создать шаблон базовый проект и добавить его в систему проектов. Также показано, как зарегистрировать этот шаблон с помощью Visual Studio с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут, который записывает полный путь к *\\Templates\Projects\SimpleProject\\* папка в системе реестр.

С помощью шаблона Visual Studio (*.vstemplate* файла) вместо базового проекта шаблона, можно управлять как шаблон появится в **новый проект** диалоговое окно, и способ параметров шаблона заменить. Объект *.vstemplate* файл — это файл XML, который описывает, как исходные файлы должны быть включены при создании проекта с помощью шаблона проекта системы. Сама система проекта создается путем сбора *.vstemplate* файл и исходные файлы в *ZIP-файл* файла и разворачивать путем копирования *ZIP-файл* в папку, Известные для Visual Studio. Эта процедура описывается более подробно далее в этом пошаговом руководстве.

1. В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], откройте SimpleProject решение, которое вы создали, следуя [Создание системы базового проекта, часть 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. В *SimpleProjectPackage.cs* Найдите атрибут ProvideProjectFactory. Замените второй параметр (имя проекта) со значением null, а четвертый параметр (путь к папке шаблонов проектов)». \\\NullPath», как показано ниже.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Добавьте XML-файл с именем *SimpleProject.vstemplate* для *\\Templates\Projects\SimpleProject\\* папки.

4. Замените содержимое файла *SimpleProject.vstemplate* следующим кодом.

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

5. В **свойства** окно, выберите все пять файлов в *\\Templates\Projects\SimpleProject\\* папку **действие при построении** Чтобы **ZipProject**.

    ![Простой проект папку](../extensibility/media/simpproj2.png "SimpProj2")

    \<TemplateData > раздел определяет расположение и внешний вид типа проекта SimpleProject в **новый проект** диалоговое окно, как показано ниже:

- \<Имя > шаблон проекта приложением SimpleProject имена элементов.

- \<Описание > элемент содержит описание, которое отображается в **новый проект** диалогового окна при выборе шаблона проекта.

- \<Значок > элемент указывает значок, который отображается вместе с SimpleProject типа проекта.

- \<ProjectType > типа проекта в имена элементов **новый проект** диалоговое окно. Это имя заменяет имя параметра атрибута ProvideProjectFactory проекта.

  > [!NOTE]
  > \<ProjectType > должен соответствовать `LanguageVsTemplate` аргумент `ProvideProjectFactory` атрибута в файле SimpleProjectPackage.cs.

  \<TemplateContent > разделе описываются эти файлы, которые создаются при создании нового проекта:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Все три файла имеют `ReplaceParameters` значение true, что позволяет замена параметров. *Program.cs* файл имеет `OpenInEditor` значение true, что приводит к файл, открываемый в редакторе кода, при создании проекта.

  Дополнительные сведения об элементах в схеме шаблона Visual Studio, см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Если проект имеет более одного шаблона Visual Studio, каждый шаблон находится в отдельной папке. Каждый файл в этой папке должен иметь **действие при построении** присвоено **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Добавление минимальным vsct-файл
 Visual Studio должна выполняться в режиме для распознавания нового или измененного шаблона Visual Studio. Режим установки требует *.vsct* файла должны присутствовать. Таким образом, необходимо добавить минимальным *.vsct* файл в проект.

1. Добавьте XML-файл с именем *SimpleProject.vsct* SimpleProject проект.

2. Замените содержимое файла *SimpleProject.vsct* файла следующим кодом.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Задайте **действие при построении** для этого файла в **VSCTCompile**. Это можно сделать только в *.csproj* файл, не видны в **свойства** окна. Убедитесь, что **действие при построении** этого файла имеет значение **None** на этом этапе.

    1. Щелкните правой кнопкой мыши папку SimpleProject и нажмите кнопку **изменить SimpleProject.csproj**.

    2. В *.csproj* файл, найдите *SimpleProject.vsct* элемента.

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Изменить действие при построении **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. файл проекта и закрыть редактор.

    5. Сохранить SimpleProject узел, а затем в **обозревателе решений** щелкните **перезагрузить проект**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Изучите шаги сборки шаблонов Visual Studio
 В системе сборки проекта VSPackage обычно выполняется Visual Studio в режиме при *.vstemplate* изменяется файл или проект, содержащий *.vstemplate* файл перестраивается. Читатели могут проследить, задав уровень детализации MSBuild в нормальное состояние или более поздней версии.

1. В меню **Сервис** выберите пункт **Параметры**.

2. Разверните **проекты и решения** узел, а затем выберите **сборка и запуск**.

3. Задайте **степень подробности сообщений при сборке проекта MSBuild** для **обычный**. Нажмите кнопку **ОК**.

4. Перестройте проект SimpleProject.

    На этапе построения для создания *ZIP-файл* файл проекта должен выглядеть следующим образом.

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
Шаблоны Visual Studio не содержат сведения о пути. Таким образом, шаблон *ZIP-файл* файл должен быть развернут в расположении, известно, что Visual Studio. Расположение папки Шаблоны_проекта обычно является *\Microsoft\VisualStudio\14.0Exp\ProjectTemplates < % LOCALAPPDATA % >*.

Чтобы развернуть свою фабрику проекта, программа установки требуются права администратора. Развертывание шаблонов в узле установки Visual Studio: *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Проверка шаблона Visual Studio
Протестируйте свою фабрику проекта, чтобы понять, каким он иерархии проекта с помощью шаблона Visual Studio.

1. Сбросьте экспериментальный экземпляр Visual Studio SDK.

    На [!INCLUDE[win7](../debugger/includes/win7_md.md)]: На **запустить** меню Найти **средств Microsoft Visual Studio или Microsoft Visual Studio SDK/** папку, а затем выберите **Сброс Microsoft Visual Studio экспериментального экземпляра**.

    В более поздних версиях Windows: На **запустить** введите **Сброс Microsoft Visual Studio \<версии > экспериментальный экземпляр**.

2. Появится окно командной строки. Когда появится слова **нажмите любую клавишу для продолжения**, нажмите кнопку **ввод**. После закрытия окна, откройте Visual Studio.

3. Перестройте проект SimpleProject и начните отладку. Откроется экспериментальный экземпляр.

4. В экспериментальном экземпляре создайте проект SimpleProject. В **новый проект** выберите **SimpleProject**.

5. Вы должны увидеть новый экземпляр класса SimpleProject.

    ![Новый экземпляр простого проекта](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Мой новый экземпляр проекта](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Создать дочерний узел типа проекта
Можно добавить дочерний узел в узел типа проекта в **новый проект** диалоговое окно. Например для типа проекта SimpleProject, могут использоваться дочерние узлы для консольных приложений, окно приложения, веб-приложений и т. д.

Дочерние узлы создаются путем изменения файла проекта и добавление \<OutputSubPath > дочерних элементов для \<ZipProject > элементы. При копировании шаблона во время сборки или развертывания каждый дочерний узел становится вложенную папку шаблонов проектов.

В этом разделе показано, как создать дочерний узел консоли для типа проекта SimpleProject.

1. Переименуйте *\\Templates\Projects\SimpleProject\\* папку  *\\Templates\Projects\ConsoleApp\\*.

2. В **свойства** окно, выберите все пять файлов в *\\Templates\Projects\ConsoleApp\\* папку и убедитесь, что **действие при построении**присваивается **ZipProject**.

3. В файле SimpleProject.vstemplate, добавьте следующую строку в конце \<TemplateData > раздела, непосредственно перед закрывающим тегом.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    В этом случае шаблон консольного приложения в дочернем узле консоли и в родительском узле SimpleProject, который находится на один уровень выше дочерний узел.

4. Сохранить *SimpleProject.vstemplate* файла.

5. В *.csproj* добавьте \<OutputSubPath > для каждого элемента ZipProject. Выгрузить проект, что и раньше и в файле проекта.

6. Найдите \<ZipProject > элементы. К каждому \<ZipProject > элемента, добавьте \<OutputSubPath > элемент и присвойте ему значение консоли. ZipProject

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

7. Добавьте этот \<PropertyGroup > в файл проекта:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Сохраните файл проекта и перезагрузить проект.

## <a name="test-the-project-type-child-node"></a>Проверить дочерний узел типа проекта
Протестировать измененный файл проекта для просмотра ли **консоли** дочерний узел отображается в **новый проект** диалоговое окно.

1. Запустите **Сброс Microsoft Visual Studio экспериментального экземпляра** средство.

2. Перестройте проект SimpleProject и начните отладку. Откроется экспериментальный экземпляр

3. В **новый проект** диалоговое окно, нажмите кнопку **SimpleProject** узла. **Консольное приложение** шаблон должен отображаться в **шаблоны** области.

4. Разверните **SimpleProject** узла. **Консоли** должен отображаться дочерний узел. **Приложения SimpleProject** шаблона остается в **шаблоны** области.

5. Нажмите кнопку **отменить** и остановить отладку.

    ![Простой проект Свертка](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Простой проект узел консоли](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Замена параметров шаблона проекта
- [Создание системы базового проекта. часть 1](../extensibility/creating-a-basic-project-system-part-1.md) было показано, как перезаписать `ProjectNode.AddFileFromTemplate` метод базовая разновидность замена параметров шаблона. В этом разделе объясняется, как использовать более сложные параметры шаблона Visual Studio.

При создании проекта с помощью шаблона Visual Studio в **новый проект** » диалогового окна «Параметры заменяются шаблон строки для настройки проекта. Параметр шаблона — это специальный маркер, который начинается и заканчивается знаком доллара, например, $time$. Следующие два параметра особенно полезны для включения настройки в проектах, основанных на шаблоне:

- $GUID [1-10] $ заменяется на новый идентификатор Guid. Можно указать до 10 уникальных GUID, например, $guid1$.

- $safeprojectname$ — это имя, указанное пользователем в **новый проект** диалоговое окно, изменить, чтобы удалить все небезопасные символы и пробелы.

  Полный список параметров шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Для замены параметров шаблона проекта

1. В *SimpleProjectNode.cs* файл, удалите `AddFileFromTemplate` метод.

2. В  *\\Templates\Projects\ConsoleApp\SimpleProject.myproj* файл, найдите \<RootNamespace > свойства и измените его значение на $safeprojectname$.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. В  *\\Templates\Projects\SimpleProject\Program.cs* файл, замените содержимое файла следующим кодом:

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

4. Перестройте проект SimpleProject и начните отладку. Откроется экспериментальный экземпляр.

5. Создайте новое SimpleProject консольное приложение. (В **типы проектов** области выберите **SimpleProject**. В разделе **установленные шаблоны Visual Studio**выберите **консольное приложение**.)

6. В только что созданный проект, откройте *Program.cs*. Он должен выглядеть примерно следующим образом (значения GUID в файле будут отличаться.):

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
Можно создать страницу свойств для данного типа проекта, чтобы пользователи могут просматривать и изменять свойства в проектах, основанных на шаблоне. В этом разделе показано, как создать страницу свойств, независимых от конфигурации. Эта страница основных свойств использует сетки свойств для отображения открытых свойств, которые предоставляют в классе страницы свойств.

Являются производными от класса страницы свойств `SettingsPage` базового класса. Сетки свойств, предоставляемых `SettingsPage` класс поддерживает большинство примитивных типов данных и знает, как для их отображения. Кроме того `SettingsPage` класс знает, как сохранить значения свойств в файл проекта.

На страницу свойств, созданные в этом разделе позволяют изменять и сохранять этих свойств проекта:

- AssemblyName

- OutputType

- RootNamespace.

1. В *SimpleProjectPackage.cs* добавьте это `ProvideObject` атрибут `SimpleProjectPackage` класса:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    При этом регистрируется класса страницы свойств `GeneralPropertyPage` в COM.

2. В *SimpleProjectNode.cs* файл, добавьте эти две переопределенные методы в `SimpleProjectNode` класса:

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

    Оба метода возвращают массив страницы свойств идентификаторов GUID. Идентификатор GUID GeneralPropertyPage является единственным элементом в массиве, поэтому **страницы свойств** диалоговое окно будет отображаться только на одной странице.

3. Добавьте файл класса с именем *GeneralPropertyPage.cs* SimpleProject проект.

4. Замените содержимое этого файла, используя следующий код:

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

    `GeneralPropertyPage` Класс предоставляет три открытых свойства AssemblyName OutputType и RootNamespace. Так как AssemblyName отсутствует метод set, он отображается как свойство только для чтения. OutputType является константа перечислимого типа, поэтому он представляется в виде раскрывающегося списка.

    `SettingsPage` Предоставляет базовый класс `ProjectMgr` для сохранения свойств. `BindProperties` Использует метод `ProjectMgr` для получения значений свойств persisted и устанавливает соответствующие свойства. `ApplyChanges` Использует метод `ProjectMgr` для получения значений свойств и сохранить их в файле проекта. Свойство значение метода задает `IsDirty` в значение true, чтобы указать, что свойства должен сохраняться. Сохраняемости происходит при сохранении проекта или решения.

5. Перестройте решение SimpleProject и начните отладку. Откроется экспериментальный экземпляр.

6. В экспериментальном экземпляре создайте новое приложение SimpleProject.

7. Visual Studio вызывает свою фабрику проекта для создания проекта с помощью шаблона Visual Studio. Новый *Program.cs* файл открыт в редакторе кода.

8. Щелкните правой кнопкой мыши узел проекта в **обозревателе решений**, а затем нажмите кнопку **свойства**. Откроется диалоговое окно **Страницы свойств**.

    ![Страница свойств проекта простой](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Проверка страницы свойств проекта
Теперь вы можете протестировать можно изменить и изменить значения свойств.

1. В **страницы свойств MyConsoleApplication** » диалогового окна «Изменение **DefaultNamespace** для **MyApplication**.

2. Выберите **OutputType** свойства, а затем выберите **библиотеки классов**.

3. Нажмите кнопку **применить**, а затем нажмите кнопку **ОК**.

4. Снова откройте **страницы свойств** диалоговое окно и убедитесь, что изменения были сохранены.

5. Закройте экспериментальный экземпляр Visual Studio.

6. Снова откройте экспериментальный экземпляр.

7. Снова откройте **страницы свойств** диалоговое окно и убедитесь, что изменения были сохранены.

8. Закройте экспериментальный экземпляр Visual Studio.
    ![Закройте экспериментальный экземпляр](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
