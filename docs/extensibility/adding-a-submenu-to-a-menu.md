---
title: Добавление подменю в меню | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6998c275aead7b12b107f700e699f5a82edd84e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102425"
---
# <a name="adding-a-submenu-to-a-menu"></a>Добавление подменю в меню
Это пошаговое руководство построено на демонстрации в [добавлению меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) , отображая Добавление подменю в **TestMenu** меню.  
  
 Подменю — это дополнительный меню, которое отображается в другом меню. Подменю могут идентифицироваться по стрелке, которая следует за его имя. Щелкнув имя приводит вложенного меню и команд для отображения.  
  
 В этом пошаговом руководстве создается подменю в меню в строке меню Visual Studio и помещает новую команду в подменю. Пошаговое руководство также реализует новой команды.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Добавление подменю в меню  
  
1.  Следуйте указаниям в [добавлению меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Создание элемента проекта и меню. В этом пошаговом руководстве предполагается, что имя проекта VSIX является `TopLevelMenu`.  
  
2.  Откройте TestCommandPackage.vsct. В `<Symbols>` добавьте `<IDSymbol>` элемент для подменю, один для подменю группы и один для команды, все в `<GuidSymbol>` узел с именем «guidTopLevelMenuCmdSet.» Это же узел, который содержит `<IDSymbol>` элемент для меню верхнего уровня.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Добавьте вновь созданный подменю `<Menus>` раздела.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Пары GUID-идентификатор родительского указывает группу меню, в котором создана [добавлению меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), и является дочерним элементом меню верхнего уровня.  
  
4.  Добавить группу меню, определенных на шаге 2 в `<Groups>` статьи и сделайте его дочерним подменю.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Добавьте новый `<Button>` элемент `<Buttons>` раздел, чтобы определить команды, созданный на шаге 2, как элемент в подменю.  
  
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
  
6.  Постройте решение и запустите отладку. Вы увидите экспериментальный экземпляр.  
  
7.  Нажмите кнопку **TestMenu** для просмотра нового подменю с именем **подменю**. Нажмите кнопку **подменю** подменю открыть и просмотреть новая команда **подкоманда теста**. Обратите внимание, что нажатие кнопки **теста подкоманда** не выполняет никаких действий.  
  
## <a name="adding-a-command"></a>Добавление команды  
  
1.  Откройте TestCommand.cs и добавьте следующий идентификатор команды после существующий идентификатор команды.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Добавьте подкоманда. Найти команду Конструктор. Добавьте следующие строки, сразу после вызова метода `AddCommand` метод.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback` Обработчик команды будут определены позже. Конструктор должен выглядеть следующим образом:  
  
    ```csharp  
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
  
3.  Добавьте SubItemCallback(). Это метод, который вызывается при выборе новой команды в подменю.  
  
    ```csharp  
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
  
4.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
5.  На **TestMenu** меню, нажмите кнопку **подменю** и нажмите кнопку **подкоманда теста**. Окно сообщения должен отображаться, а также отображать текст «Теста команда внутри TestCommand.SubItemCallback()».  
  
## <a name="see-also"></a>См. также  
 [Добавление меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
