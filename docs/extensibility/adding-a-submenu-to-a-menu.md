---
title: "Добавление подменю в меню | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "контекстные меню"
  - "подменю, каскадных"
  - "каскадные подменю"
  - "меню, Создание каскадных подменю"
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 43
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 43
---
# Добавление подменю в меню
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Данного пошагового руководства лежит демонстрации в [Добавление меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) показывая, как добавить подменю для **TestMenu** меню.  
  
 Подменю является вторым меню в другое меню. Подменю можно идентифицировать по стрелке, которая соответствует его имени. Если щелкнуть имя вызывает меню и команд для отображения.  
  
 В этом пошаговом руководстве создается подменю в меню в строке меню Visual Studio и помещает новую команду в подменю. Пошаговое руководство также реализует новую команду.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Добавление подменю в меню  
  
1.  Следуйте указаниям [Добавление меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) для создания элемента проекта и меню. В этом пошаговом руководстве предполагается, что имя проекта VSIX — `TopLevelMenu`.  
  
2.  Откройте TestCommandPackage.vsct. В `<Symbols>` Добавьте `<IDSymbol>` элемент для подменю, один для группы подменю и один для команды, в `<GuidSymbol>` узел с именем «guidTopLevelMenuCmdSet.» Это же узел, содержащий `<IDSymbol>` элемент меню верхнего уровня.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Вновь созданный подменю, чтобы добавить `<Menus>` раздел.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Указывает пару GUID\-идентификатор родительского объекта группы меню, в котором создана [Добавление меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), и является дочерним для элемента меню верхнего уровня.  
  
4.  Добавление группы меню, определенных на шаге 2 `<Groups>` статьи и сделайте его дочерним подменю.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Добавить новую `<Button>` элемент `<Buttons>` раздел, чтобы определить команду, созданный на этапе 2 элемент подменю.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  Постройте решение и запустить отладку. Вы должны увидеть экспериментальный экземпляр.  
  
7.  Щелкните **TestMenu** для просмотра нового подменю с именем **подменю**. Щелкните **подменю** откройте подменю и отображается новый пункт **тестирования подкоманда**. Обратите внимание, что нажатие кнопки **тестирования подкоманда** не выполняет никаких действий.  
  
## Добавление команды  
  
1.  Откройте TestCommand.cs и добавьте следующий код команды после существующий идентификатор команды.  
  
    ```c#  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Добавьте подкоманда. Найти команду Конструктор. Добавьте следующие строки сразу после вызова `AddCommand` метод.  
  
    ```c#  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback` Обработчик команды будут определены в дальнейшем. Конструктор теперь должен выглядеть следующим образом:  
  
    ```c#  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Добавьте SubItemCallback\(\). Это метод, который вызывается при щелчке новую команду в подменю.  
  
    ```c#  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен отображаться.  
  
5.  На **TestMenu** меню, щелкните **подменю** и нажмите кнопку **тестирования подкоманда**. Окно сообщения должен присутствовать и отображать текст «Тест команды внутри TestCommand.SubItemCallback\(\)».  
  
## См. также  
 [Добавление меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)