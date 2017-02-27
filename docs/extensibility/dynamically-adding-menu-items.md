---
title: "Динамическое добавление элементов меню | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DYNAMICITEMSTART"
  - "пункты меню, динамическое добавление"
  - "Добавление динамических элементов меню"
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 37
---
# Динамическое добавление элементов меню
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно добавить элементы меню во время выполнения, указав `DynamicItemStart` команды флаг определения кнопку заполнитель в файле \(.vsct\) таблицы команд Visual Studio, то номера \(в коде\) меню элементы для отображения и обработки команды. После загрузки VSPackage заполнителя заменяется пунктов динамического меню.  
  
 Visual Studio использует динамические списки в **недавно использованные** списка \(MRU\), которая отображает имена, недавно открывавшихся документов, и **Windows** список, который отображает имена окон, открытых в настоящий момент.`DynamicItemStart` Определения команды флаг указывает, что команда заполнитель пока открыт VSPackage. При открытии VSPackage заполнителя заменяется 0 или несколько команд, которые создаются во время выполнения и добавляются к списку динамической. Вы не сможете положение отображается в меню, где отображается динамический список, пока открыт VSPackage. Чтобы заполнить динамический список, Visual Studio запрашивает VSPackage искать команды с Идентификатором, первый символы которой являются таким же, как идентификатор заполнителя. Если Visual Studio обнаружит соответствующей команды, он добавляет имя команды динамического списка. Затем увеличивает идентификатор и ищет другой соответствующей команды для добавления динамического списка, пока не останется больше нет динамических команд.  
  
 В этом пошаговом руководстве показано, как задать запускаемый проект в решении Visual Studio с помощью команды **обозревателе решений** инструментов. Он использует контроллер меню с динамической раскрывающегося списка проекты активного решения. Для предотвращения этой команды при решения не открыт, или если открыть решение содержит только один проект, VSPackage загружается только в том случае, если решение содержит несколько проектов.  
  
 Дополнительные сведения о vsct\-файлах см. в разделе [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Создание расширения с помощью команды меню  
  
1.  Создайте проект VSIX с именем `DynamicMenuItems`.  
  
2.  При открытии проекта, добавление шаблона элемента пользовательской команды и назовите его **DynamicMenu**. Для получения дополнительной информации см. [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Настройка элементов в файле .vsct  
 Чтобы создать контроллер меню с пунктов динамического меню на панели инструментов, необходимо указать следующие элементы:  
  
-   Две команды группы, содержащей меню контроллера и другой, содержащий пункты меню в раскрывающемся списке  
  
-   Элемент меню одного типа `MenuController`  
  
-   Две кнопки, которая выступает в качестве заполнителя для элементов меню и другой, предоставляющий значок и подсказки на панели инструментов.  
  
1.  В DynamicMenuPackage.vsct определение идентификаторов команд. Перейдите к разделу символы и замените элементы IDSymbol **guidDynamicMenuPackageCmdSet** GuidSymbol блок. Необходимо определить элементы IDSymbol для двух групп, контроллера меню, команда заполнитель и команда привязки.  
  
    ```c#  
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
  
2.  В разделе группы удалите существующие группы и добавьте две группы, определенного ранее:  
  
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
  
     Добавьте MenuController. Установите флаг команды DynamicVisibility, поскольку не всегда отображается. ButtonText не отображается.  
  
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
  
     Родительский элемент заполнителя кнопки **MyMenuControllerGroup**. Добавление параметров командной строки DynamicItemStart, DynamicVisibility и TextChanges к кнопке заполнителя. ButtonText не отображается.  
  
     Кнопка привязки содержит значок и текст всплывающей подсказки. Также является родительской привязки кнопки **MyMenuControllerGroup**. Добавляется флаг NoShowOnMenuController команды, чтобы убедиться в том, что кнопки не отображается в раскрывающемся меню контроллера и флаг команды FixMenuController вносить постоянные привязки.  
  
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
  
4.  Добавить значок в проект \(в папку «ресурсы»\) и затем добавьте ссылку на него в файле .vsct. В этом пошаговом руководстве мы используем значок стрелки, включенный в шаблон проекта.  
  
5.  Добавьте раздел VisibilityConstraints за пределами раздела команд непосредственно перед разделом символы. \(Может появиться предупреждение при добавлении после символов.\) В этом разделе гарантирует, что контроллер меню отображается только при загрузке решения с несколькими проектами.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## Реализация динамического меню команды  
 Создание динамического меню команду класс, наследуемый от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. В этой реализации конструктор указывает предикат, используемый для сопоставления команд. Необходимо переопределить <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> метод с помощью следующего предиката задать <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> Свойства, которое определяет команду, чтобы вызывать.  
  
1.  Создайте новый файл класса C\# с именем DynamicItemMenuCommand.cs и добавьте класс с именем **DynamicItemMenuCommand** наследуемый от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```c#  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Добавьте следующие операторы using:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Добавьте закрытое поле для хранения предикат соответствия:  
  
    ```c#  
    private Predicate<int> matches;  
  
    ```  
  
4.  Добавьте конструктор, который наследует от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> конструктор и указывает на обработчик команды и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчика. Добавьте предикат для сопоставления команды:  
  
    ```c#  
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
  
5.  Переопределение <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> метод соответствия вызове предиката и задает <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> Свойства:  
  
    ```c#  
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
  
## Добавление команды  
 Конструктор DynamicMenu — где настроить команды меню, включая динамическое меню и пунктов меню.  
  
1.  В DynamicMenuPackageGuids.cs добавьте идентификатор GUID набора команд и идентификатор команды:  
  
    ```c#  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  В файле DynamicMenu.cs добавьте следующие операторы using:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  В классе DynamicMenu добавьте закрытое поле **dte2**.  
  
    ```c#  
    private DTE2 dte2;  
    ```  
  
4.  Добавьте закрытый rootItemId поля:  
  
    ```c#  
    private int rootItemId = 0;  
    ```  
  
5.  В конструкторе DynamicMenu добавьте команду меню. В следующем разделе мы определим обработчик команды `BeforeQueryStatus` обработчик событий и предикат совпадения.  
  
    ```c#  
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
  
## Реализация обработчиков  
 Для реализации пунктов динамического меню на контроллере меню, необходимо обработать команду при щелчке динамического элемента. Необходимо также реализовать логику, которая задает состояние элемента меню. Добавьте в класс DynamicMenu обработчиков.  
  
1.  Для реализации **установить запускаемый проект** команды, добавьте **OnInvokedDynamicItem** обработчик событий. Он ищет проекта, имя которого совпадает с текстом команды, как был вызван и устанавливает его в качестве запускаемого проекта, задав полный путь <xref:EnvDTE.SolutionBuild.StartupProjects%2A> свойство.  
  
    ```c#  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
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
  
2.  Добавление `OnBeforeQueryStatusDynamicItem` обработчика событий. Это обработчик вызывается перед `QueryStatus` события. Он определяет, является ли элемент меню «реальными» элемент, то есть не заполнитель элемента, и элемент уже установлен ли \(это означает, что проект уже задано как автозагружаемый проект\).  
  
    ```c#  
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
  
## Реализация предикат соответствия идентификатор команды  
  
1.  Теперь можно реализуйте предикат совпадения. Нам необходимо определить следующее: во\-первых, следует ли команда идентификатор допустим \(это больше или равно идентификатору объявленный команды\), а во\-вторых, определяет ли возможно проекта \(он меньше, чем число проектов в решении\).  
  
    ```c#  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## Параметр VSPackage для загрузки только в том случае, если решение содержит несколько проектов  
 Поскольку **установить запускаемый проект** команда не имеет смысла Если активное решение содержит несколько проектов, можно настроить VSPackage, чтобы автоматически загружать только в этом случае. Используется <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> с контекстом пользовательского интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. В файле DynamicMenuPackage.cs добавьте следующие атрибуты к классу DynamicMenuPackage:  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## Тестирование команды установить запускаемый проект  
 Теперь можно проверить код.  
  
1.  Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен отображаться.  
  
2.  В экспериментальном экземпляре откройте решение, которое содержит более одного проекта.  
  
     Вы увидите значок стрелки на **обозревателе решений** инструментов. При развертывании, появится меню, которые представляют разные проекты в решении.  
  
3.  Если выбрать один из проектов, становится Автозагружаемый проект.  
  
4.  Если закрыть решение или откройте решение, которое содержит только один проект, значок панели инструментов должна исчезнуть.  
  
## См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)