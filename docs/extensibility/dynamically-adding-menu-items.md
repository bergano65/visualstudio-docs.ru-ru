---
title: Динамическое добавление элементов меню Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4387c1930e09e49c0ec5c36ccedc1bb83dc273f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712056"
---
# <a name="dynamically-add-menu-items"></a>Динамически добавляйте элементы меню
Вы можете добавить элементы меню `DynamicItemStart` во время выполнения, указав флаг команды на определении кнопки заполнителя в командном столе Visual Studio *(.vsct)* файл, а затем определив (в коде) количество элементов меню для отображения и обработки команды (ы). При загрузке VSPackage заполнитель заменяется динамическими пунктами меню.

 Visual Studio использует динамические списки в списке **Most Recently Used** (MRU), в котором отображаются имена документов, которые были открыты недавно, и список **Windows,** который отображает имена окон, которые в настоящее время открыты.   Флаг `DynamicItemStart` в определении команды определяет, что команда является заполнителем до открытия VSPackage. При открытии VSPackage заменяется 0 или более команд, которые создаются во время выполнения и добавляются в динамический список. Возможно, вы не сможете увидеть позицию в меню, где динамический список появляется до открытия VSPackage.  Чтобы заполнить динамический список, Visual Studio просит VSPackage искать команду с идентификатором, первые символы которого совпадают с идентификатором заполнителя. Когда Visual Studio находит соответствующую команду, она добавляет имя команды в динамический список. Затем он приращает идентификатор и ищет другую соответствующую команду, чтобы добавить в динамический список, пока нет более динамических команд.

 В этом пошаговом слове показано, как настроить проект запуска в решении Visual Studio с командой на панели инструментов **Solution Explorer.** Он использует контроллер меню, который имеет динамический список выпадающих проектов в активном решении. Чтобы эта команда не появлялась, когда решение не открыто или когда открытое решение имеет только один проект, VSPackage загружается только тогда, когда решение имеет несколько проектов.

 Для получения дополнительной информации о [Visual Studio command table (.vsct) files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) *файлах .vsct* см.

## <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с командой меню

1. Создайте проект VSIX под названием `DynamicMenuItems`.

2. Когда проект откроется, добавьте шаблон пользовательского элемента команд и назовите его **DynamicMenu.** Для получения дополнительной информации [см. Создать расширение с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Настройка элементов в файле *.vsct*
 Чтобы создать контроллер меню с динамическими элементами меню на панели инструментов, вы указываете следующие элементы:

- Две группы команд, одна из них содержит контроллер меню, а другая содержит элементы меню в выпадающем

- Один элемент меню типа`MenuController`

- Две кнопки, одна, которая выступает в качестве заполнителя для элементов меню, а другая, которая поставляет значок и набор инструментов на панели инструментов.

1. В *DynamicMenuPackage.vsct*определите идевы команд. Перейдите в раздел Символы и замените элементы IDSymbol в блоке **guidDynamicMenuPackageCmdSet** GuidSymbol. Элементы IDSymbol необходимо определить для двух групп, контроллер меню, команду заполнителя и команду якоря.

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. В разделе Группы удалите существующие группы и добавьте только что определенные группы:

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     Добавьте MenuController. Установите флаг команды DynamicVisibility, так как он не всегда виден. КнопкаТекст не отображается.

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. Добавьте две кнопки, одну в качестве заполнителя для динамических элементов меню и одну в качестве якоря для MenuController.

     Родительским элементом кнопки заполнителя является **MyMenuControllerGroup.** Добавьте в кнопку заполнителя флаги DynamicItemStart, DynamicVisibility и TextChanges. КнопкаТекст не отображается.

     Кнопка якоря держит значок и текст tooltip. Родитель кнопки якоря также **MyMenuControllerGroup**. Вы добавляете флаг команды NoShowOnMenuController, чтобы убедиться, что кнопка на самом деле не появляется в диспетчере меню, и флаг команды FixMenuController, чтобы сделать ее постоянным якорем.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. Добавьте значок в проект (в папке *Ресурсов),* а затем добавьте ссылку на него в *файле .vsct.* В этом пошаговом шаге мы используем значок Стрелки, включенный в шаблон проекта.

5. Добавьте раздел VisibilityConstraints за пределами раздела Команд непосредственно перед разделом Символы. (Вы можете получить предупреждение, если вы добавите его после символов.) Этот раздел гарантирует, что контроллер меню появляется только при загрузке решения с несколькими проектами.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Реализация динамической команды меню
 Вы создаете динамический класс <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>команд меню, который наследует от . В этой реализации конструктор определяет предикат, который будет использоваться для сопоставления команд. Необходимо переопределить <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> метод использования этого предиката <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> для установки свойства, которое определяет вызов команды.

1. Создайте новый файл класса C' по имени *DynamicItemMenuCommand.cs*и добавьте <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>класс под названием **DynamicItemMenuCommand,** который наследует:

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Добавьте следующие директивы using.

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Добавьте частное поле для хранения предиката матча:

    ```csharp
    private Predicate<int> matches;

    ```

4. Добавьте конструктор, который наследует от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> конструктора и определяет обработчик команды и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчик. Добавьте предикат для соответствия команде:

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. Переопределить <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> метод так, чтобы он вызывает предикат совпадений и устанавливает свойство: <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>Добавление команды
 Конструктор DynamicMenu — это место, где настраиваются команды меню, включая динамическое меню и пункты меню.

1. В *DynamicMenuPackage.cs*добавьте GUID набора команд и идентификатор команды:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. В *DynamicMenu.cs* файле добавьте следующие директивы:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. В `DynamicMenu` классе добавьте частное поле **dte2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Добавьте частное поле rootItemId:

    ```csharp
    private int rootItemId = 0;
    ```

5. В конструкторе DynamicMenu добавьте команду меню. В следующем разделе мы определим обработчик команд, обработчик `BeforeQueryStatus` событий и предикат соответствия.

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>Реализация обработчиков
 Для реализации динамических элементов меню на контроллере меню необходимо обрабатывать команду при нажатии динамического элемента. Необходимо также реализовать логику, которая устанавливает состояние элемента меню. Добавьте обработчики в `DynamicMenu` класс.

1. Для реализации команды Set **Startup Project** добавьте обработчик событий **OnInvokedDynamicItem.** Он ищет проект, название которого совпадает с текстом вызываемых команд, и устанавливает его в качестве <xref:EnvDTE.SolutionBuild.StartupProjects%2A> проекта запуска, устанавливая его абсолютный путь в свойстве.

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. Добавьте `OnBeforeQueryStatusDynamicItem` обработчик событий. Это обработчик, `QueryStatus` вызванный перед событием. Он определяет, является ли элемент меню «реальным» элементом, т.е. не элементом заполнителя, и проверен ли элемент (имеется в виду, что проект уже установлен как проект запуска).

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>Реализация предиката соответствия идентификатора команды

Теперь реализуем предикат матча. Нам нужно определить две вещи: во-первых, является ли идентификатор команды действительным (он больше или равен заявленного идентификатору команды), и, во-вторых, указывает ли он возможный проект (это меньше, чем количество проектов в решении).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Установите VSPackage для загрузки только тогда, когда решение имеет несколько проектов
 Поскольку команда **Set Startup Project** не имеет смысла, если у активного решения не более одного проекта, можно настроить VSPackage на автоматическую загрузку только в этом случае. Вы <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> используете вместе с <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>контекстом uI . В *DynamicMenuPackage.cs* файле добавьте следующие атрибуты в класс DynamicMenuPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Протестировать команду проекта запуска установки
 Теперь вы можете проверить свой код.

1. Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен появиться.

2. В экспериментальном примере откройте решение, которое имеет несколько проектов.

     Вы должны увидеть значок стрелки на панели инструментов **Solution Explorer.** При его расширении должны отображаться элементы меню, представляющие различные проекты в решении.

3. Когда вы проверяете один из проектов, он становится стартап-проектом.

4. При закрытии решения или открытии решения, в рамках которого есть только один проект, значок панели инструментов должен исчезнуть.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
- [Как VSPackages добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
