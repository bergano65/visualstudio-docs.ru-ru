---
title: "Динамическое добавление пунктов меню | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb79bfa9938aade8ff138817073fad4897276184
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="dynamically-adding-menu-items"></a>Динамическое добавление пунктов меню
Пункты меню можно добавить во время выполнения, указав `DynamicItemStart` команды флаг в определении кнопки заполнитель в файле (.vsct) таблицы команд Visual Studio, то определение (в коде) число меню элементы для отображения и обработки команды. При загрузке VSPackage заполнителя заменяется пунктов динамического меню.  
  
 Visual Studio использует динамические списки в **недавно использовавшиеся** (MRU) список, в котором отображаются имена, недавно открывавшихся документов, и **Windows** список, который отображает имена окон открытых в данный момент.   `DynamicItemStart` Флаг для определения команды указывает, что команда является заполнителя, пока не будет открыт VSPackage. При открытии пакета VSPackage заполнителя заменяется 0 или несколько команд, которые создаются во время выполнения и добавляется к списку динамического. Вы не сможете положение отображается в меню, где отображается динамический список, пока не будет открыт VSPackage.  Чтобы заполнить динамический список, Visual Studio предлагает VSPackage, чтобы найти команду с Идентификатором первого символы которых совпадают с идентификатор заполнителя. Если Visual Studio обнаружит соответствующей команды, имя команды добавляет динамического списка. Затем увеличивает идентификатор и ищет сопоставления другую команду, чтобы добавить динамический список, пока не будут больше нет динамических команд.  
  
 В этом пошаговом руководстве показано, как задание запускаемого проекта в решении Visual Studio с помощью команды на **обозревателе решений** инструментов. Он использует контроллер меню с динамической раскрывающийся список проектов в активном решении. Для сохранения этой команды будут отображаться, когда ни одно решение открыто или при открытом решении имеет только один проект, пакет VSPackage загружаются только в том случае, если решение содержит несколько проектов.  
  
 Дополнительные сведения о vsct-файлами см. в разделе [Visual Studio Command Table (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню  
  
1.  Создайте проект VSIX с именем `DynamicMenuItems`.  
  
2.  При открытии проекта, Добавление пользовательской команды шаблона элемента и назовите его **DynamicMenu**. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>Настройка элементов в vsct-файле  
 Чтобы создать контроллер меню пунктов динамического меню на панели инструментов, необходимо указать следующие элементы:  
  
-   Две команды, группы, содержащей контроллер меню и другой, содержащий пункты меню в раскрывающемся списке  
  
-   Элемент меню одного типа`MenuController`  
  
-   Две кнопки, который выступает в качестве заполнителя для пунктов меню и другой, предоставляющий значок и подсказку на панели инструментов.  
  
1.  В DynamicMenuPackage.vsct определение идентификаторов команд. Перейдите к разделу символы и заменить элементы IDSymbol в **guidDynamicMenuPackageCmdSet** GuidSymbol блока. Необходимо определить IDSymbol элементы для двух групп, контроллер меню, команда заполнитель и команда привязки.  
  
    ```csharp  
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
  
2.  В разделе "группы" Удаление существующих групп и добавьте две группы, который вы только что определили:  
  
    ```  
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
  
     Добавьте MenuController. Установите флаг команды DynamicVisibility, так как она не всегда видны. ButtonText не отображается.  
  
    ```  
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
  
3.  Добавьте две кнопки: как заполнитель для пунктов динамического меню и как привязку для MenuController.  
  
     Родительский кнопка заполнителя — **MyMenuControllerGroup**. Добавьте флаги команды DynamicItemStart, DynamicVisibility и TextChanges на кнопку заполнителя. ButtonText не отображается.  
  
     Кнопка привязки содержит значок и текст всплывающей подсказки. Родитель кнопка привязки также является **MyMenuControllerGroup**. Добавляется флаг NoShowOnMenuController команды, чтобы убедиться в том, что кнопки фактически не отображается в раскрывающемся меню контроллера и флаг команды FixMenuController вносить постоянные привязки.  
  
    ```  
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
  
4.  Добавить значок в проект (в папке Resources) и затем добавьте ссылку на него в vsct-файле. В этом пошаговом руководстве мы используем значок стрелки, который включен в шаблоне проекта.  
  
5.  Добавьте раздел VisibilityConstraints за пределами разделе команд непосредственно перед разделом символы. (Может появиться предупреждение при добавлении после символов.) В этом разделе гарантирует, что контроллер меню отображается только при загрузке решения с несколькими проектами.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>Реализация команды меню, динамические  
 Создайте класс динамического меню команды, который наследует от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. В этой реализации конструктор указывает предикат, используемый для сопоставления команд. Необходимо переопределить <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> метод с помощью предиката задать <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> свойства, которое идентифицирует вызывать команду.  
  
1.  Создайте новый файл класса C# с именем DynamicItemMenuCommand.cs и добавьте класс с именем **DynamicItemMenuCommand** , наследуемый от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Добавьте следующие операторы using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Добавьте закрытое поле для хранения предикат соответствия:  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  Добавьте конструктор, который наследует от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> конструктор и указывает, является допустимым обработчиком команд и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчика. Добавьте предикат для сопоставления команды:  
  
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
  
5.  Переопределить <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> вызове совпадения предикат и задает метод <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> свойство:  
  
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
  
## <a name="adding-the-command"></a>Добавление команды  
 Конструктор DynamicMenu — где настроить команды меню, включая динамического меню и команды меню.  
  
1.  В DynamicMenuPackageGuids.cs добавьте идентификатор GUID набора команд и идентификатор команды.  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  В файле DynamicMenu.cs добавьте следующие операторы using:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  В классе DynamicMenu добавьте закрытое поле **dte2**.  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  Добавьте поле закрытого rootItemId:  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  В конструкторе DynamicMenu добавьте команду меню. В следующем разделе мы определим обработчик команд `BeforeQueryStatus` обработчик событий и предикат совпадения.  
  
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
  
## <a name="implementing-the-handlers"></a>Реализация обработчиков  
 Чтобы реализовать пунктов динамического меню на контроллер меню, должен обрабатывать команды при щелчке динамического элемента. Также необходимо реализовать логику, которая задает состояние элемента меню. Добавьте в класс DynamicMenu обработчиков.  
  
1.  Для реализации **установить запускаемый проект** команды, добавить **OnInvokedDynamicItem** обработчик событий. Выполняет поиск проекта, имя которого совпадает с текст команды, который был вызван и задает его в качестве запускаемого проекта, задав полный путь <xref:EnvDTE.SolutionBuild.StartupProjects%2A> свойство.  
  
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
  
2.  Добавить `OnBeforeQueryStatusDynamicItem` обработчика событий. Этот метод является обработчиком, вызывается перед `QueryStatus` событий. Он определяет, является ли элемент меню элементом «real», то есть не местозаполнитель элемента, и установлен ли флажок элемента уже (что означает, что проект уже задано в качестве запускаемого проекта).  
  
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
  
## <a name="implementing-the-command-id-match-predicate"></a>Реализация предикат соответствия идентификатор команды  
  
1.  Теперь реализуют предикат совпадения. Нам необходимо определить следующее: во-первых, следует ли идентификатор команды является допустимым (это больше или равным идентификатору объявленный команды) и второй, задает ли возможных проекта (он меньше, чем число проектов в решении).  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Установка пакета VSPackage для загрузки только в том случае, если решение содержит несколько проектов  
 Поскольку **установить запускаемый проект** команда не имеет смысла, если только активное решение содержит несколько проектов, можно задать для вашего VSPackage, чтобы автоматически загружать только в этом случае. Вы используете <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> вместе с контекстом пользовательского интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. В файле DynamicMenuPackage.cs добавьте следующие атрибуты к классу DynamicMenuPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>Тестирование команды установить запускаемый проект  
 Теперь можно проверить код.  
  
1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
2.  В экспериментальном экземпляре откройте решение, которое содержит более одного проекта.  
  
     Вы увидите значок со стрелкой **обозревателе решений** инструментов. При развертывании, появится меню, которые представляют разные проекты в решении.  
  
3.  Если выбран один из проектов, оно становится запускаемый проект.  
  
4.  Если закрыть решение или откройте решение, которое содержит только один проект, должна исчезнуть значок панели инструментов.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)