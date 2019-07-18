---
title: Динамическое добавление элементов меню | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ff05de5cfd6dfa01f8e93f22f9ac09b8e61575
ms.sourcegitcommit: 3cc73e74921a9ceb622542e0e263abeebc455c00
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67624471"
---
# <a name="dynamically-add-menu-items"></a>Динамическое добавление элементов меню
Можно добавить элементы меню во время выполнения, указав `DynamicItemStart` команду флаг определения кнопку заполнитель в таблицы команд Visual Studio ( *.vsct*) файл, то определение (в коде) количество элементов меню для отображения и Обработка команды. При загрузке VSPackage, заполнитель будет заменен пунктов динамического меню.

 Visual Studio использует динамические списки в **недавно использовавшиеся** список (MRU), который отображает имена документов, которые недавно были открыты, и **Windows** список, который отображает имена окон открыты в настоящий момент.   `DynamicItemStart` Флаг для определения команды указывает, что команда является заполнителем, пока не будет открыта VSPackage. При открытии пакета VSPackage, заполнитель будет заменен 0 или больше команд, которые создаются во время выполнения и добавляются к динамическим списком. Вы не сможете см. в разделе Позиция меню, где отображается динамический список, пока не будет открыта VSPackage.  Чтобы заполнить список динамического, Visual Studio предлагает VSPackage, чтобы найти команду с Идентификатором, первые символы такие же, как идентификатор заполнителя. Когда Visual Studio находит соответствующей команды, он добавляет имя команды динамического списка. Затем увеличивает идентификатор и ищет соответствующий другую команду, чтобы добавить динамический список, пока существует не более динамичной команды.

 В этом пошаговом руководстве демонстрируется задание запускаемого проекта в решении Visual Studio с помощью команды на **обозревателе решений** панели инструментов. Он использует контроллер меню со списком динамических раскрывающегося списка проектов в активном решении. Срок действия этой команды при ни одно решение открыто, или при открытом решении имеет только один проект, VSPackage загружаются только в том случае, если решение содержит несколько проектов.

 Дополнительные сведения о *.vsct* файлы, см. в разделе [Visual Studio командные table (.vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню

1. Создайте проект VSIX с именем `DynamicMenuItems`.

2. При открытии проекта, Добавление пользовательской команды шаблона элемента и назовите его **DynamicMenu**. Дополнительные сведения см. в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Настройка элементов в *.vsct* файла
 Чтобы создать контроллер меню с помощью пунктов динамического меню на панели инструментов, необходимо указать следующие элементы:

- Две команды, группы, той, которая содержит контроллер меню и еще одно, которое содержит элементы меню, в раскрывающемся списке

- Элемент меню для одного типа `MenuController`

- Две кнопки, которая выступает в качестве заполнителя для пунктов меню, а другой, предоставляющий значок и подсказку на панели инструментов.

1. В *DynamicMenuPackage.vsct*, определение идентификаторов команд. Перейдите к разделу символы и замените элемент IDSymbol в **guidDynamicMenuPackageCmdSet** GuidSymbol блока. Необходимо определить элементы IDSymbol для двух групп, контроллер меню, заполнитель команда и команда привязки.

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

2. В разделе "группы" удалите существующие группы и добавьте две группы, который вы только что определили:

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

     Добавьте MenuController. Задайте флаг команды DynamicVisibility, так как она не всегда отображается. ButtonText не отображается.

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

3. Добавьте две кнопки: как заполнитель для пунктов динамического меню и как привязку для MenuController.

     Является родительским для объекта кнопки заполнитель **MyMenuControllerGroup**. Добавьте флаги команды DynamicItemStart DynamicVisibility и TextChanges на кнопку заполнителя. ButtonText не отображается.

     Кнопка привязки содержит значок и текст всплывающей подсказки. Также является родительским для объекта кнопки привязки **MyMenuControllerGroup**. Добавьте флаг NoShowOnMenuController команды, чтобы убедиться в том, что кнопки не отображается в раскрывающемся меню контроллера и флаг FixMenuController команды, чтобы сделать ее постоянной привязку.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->
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

4. Добавить значок в проект (в *ресурсы* папку), а затем добавьте ссылку на него в *.vsct* файла. В этом пошаговом руководстве мы используем значок стрелки, включенный в шаблон проекта.

5. Добавьте раздел VisibilityConstraints за пределами раздела команд непосредственно перед разделе "символы". (Может появиться предупреждение при добавлении после символов.) В этом разделе гарантирует, что контроллер меню отображается только при загрузке решения с несколькими проектами.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Реализации динамического меню команды
 Создайте класс команды динамическое меню, который наследует от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. В данном случае конструктор указывает предикат, который необходимо использовать для сопоставления команд. Необходимо переопределить <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> метод, используемый для задания этого предиката <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> свойство, которое определяет команду для вызова.

1. Создайте новый класс файл C#, с именем *DynamicItemMenuCommand.cs*, и добавьте класс с именем **DynamicItemMenuCommand** , наследуемый от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Добавьте следующие операторы using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Добавьте закрытое поле для хранения предикат соответствия:

    ```csharp
    private Predicate<int> matches;

    ```

4. Добавьте конструктор, который наследует от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> конструктор и определяет обработчик команд и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчика. Добавьте предикат для сопоставления команды:

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

5. Переопределить <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> метод, поэтому он вызывает совпадения предиката и наборы <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> свойство:

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

## <a name="add-the-command"></a>Добавьте команду
 Конструктор DynamicMenu является, предназначенный для настройки команды меню, включая динамические меню и пунктов меню.

1. В *DynamicMenuPackage.cs*, добавьте идентификатор GUID набора команд и идентификатор команды:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. В *DynamicMenu.cs* добавьте следующие операторы using:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. В `DynamicMenu` добавьте закрытое поле **dte2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Добавление частного rootItemId поля:

    ```csharp
    private int rootItemId = 0;
    ```

5. В конструкторе DynamicMenu добавьте команду меню. В следующем разделе мы определим обработчик команды `BeforeQueryStatus` обработчик событий, а предикат совпадения.

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

## <a name="implement-the-handlers"></a>Реализуйте обработчики
 Чтобы реализовать пунктов динамического меню на контроллере меню, необходимо обработать команду при щелчке динамического элемента. Также необходимо реализовать логику, которая задает состояние элемента меню. Добавьте обработчики для `DynamicMenu` класса.

1. Для реализации **установить запускаемый проект** команды, добавьте **OnInvokedDynamicItem** обработчик событий. Он ищет проекта, имя которого совпадает с текст команды, который был вызван и устанавливает его в качестве запускаемого проекта, задав полный путь <xref:EnvDTE.SolutionBuild.StartupProjects%2A> свойство.

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

2. Добавление `OnBeforeQueryStatusDynamicItem` обработчик событий. Это обработчик вызывается перед `QueryStatus` событий. Он определяет, является ли элемент меню элемент «настоящих», то есть не заполнитель элемента, и установлен ли флажок элемента уже (это означает, что проект уже задан в качестве запускаемого проекта).

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

## <a name="implement-the-command-id-match-predicate"></a>Реализуйте предикат совпадение идентификатор команды

Теперь реализуйте предикат совпадения. Нам нужно определить следующее: во-первых, следует ли идентификатор команды является допустимым (это больше или равным идентификатору объявленный команды), а во-вторых, определяет ли проекта (это меньше, чем число проектов в решении).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Задайте VSPackage для загрузки только в том случае, если решение содержит несколько проектов
 Так как **установить запускаемый проект** команда не имеет смысла, если только активное решение имеет более одного проекта, можно настроить автоматически загружать только в этом случае в VSPackage. Использовании <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> с контекстом пользовательского интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. В *DynamicMenuPackage.cs* файла добавьте следующие атрибуты к классу DynamicMenuPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Тестирование команды set запуска проекта
 Теперь можно протестировать код.

1. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

2. В экспериментальном экземпляре откройте решение, включающее несколько проектов.

     Вы увидите значок со стрелкой на **обозревателе решений** панели инструментов. При развертывании, появится меню, которые представляют разные проекты в решении.

3. Если выбран один из проектов, он становится запускаемого проекта.

4. При закрытии решения, или открыть решение, которое имеет только один проект, значок панели управления должна исчезнуть.

## <a name="see-also"></a>См. также
- [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
- [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)