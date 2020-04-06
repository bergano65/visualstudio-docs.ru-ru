---
title: Добавление Submenu в меню Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740266"
---
# <a name="add-a-submenu-to-a-menu"></a>Добавить Submenu в меню
Это пошаговое решение основано на демонстрации в добавлении меню в [меню Visual Studio Bar,](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) показывая, как добавить подменю в меню **TestMenu.**

 Submenu — это вторичное меню, которое отображается в другом меню. Подменю может быть идентифицировано по стрелке, которая следует за его именем. Нажатие на имя приводит к отображению подменю и его команд.

 Это пошаговое польное решение создает подменю в меню в меню Visual Studio и ставит новую команду на submenu. Пошаговая часть также реализует новую команду.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="add-a-submenu-to-a-menu"></a>Добавить Submenu в меню

1. Выполните последующие шаги в [добавлении меню в меню Visual Studio Bar](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) для создания элемента проекта и меню. Шаги в этом пошаговом шаге предполагают, `TopLevelMenu`что название проекта VSIX .

2. Открытый *TestCommandPackage.vsct*. В `<Symbols>` разделе добавьте `<IDSymbol>` элемент для подменю, один для группы submenu и один `<GuidSymbol>` для команды, все в уде под названием "guidTopLevelMenuCmdSet". Это тот же узла, `<IDSymbol>` который содержит элемент для меню верхнего уровня.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Добавьте в раздел вновь созданное `<Menus>` подменю.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     Пара GUID/ID родителя определяет группу меню, которая была создана в [Добавлении меню в меню Visual Studio Bar](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)и является ребенком меню верхнего уровня.

4. Добавьте в `<Groups>` раздел группу меню, определенную в шаге 2, и сделайте его ребенком подменю.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Добавьте `<Button>` новый `<Buttons>` элемент в раздел, чтобы определить команду, созданную в шаге 2, как элемент в подменю.

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

6. Постройте решение и запустите отладку. Вы должны увидеть экспериментальный экземпляр.

7. Нажмите **TestMenu,** чтобы увидеть новое подменю под названием **Sub Menu**. Нажмите **Sub Меню,** чтобы открыть подменю и увидеть новую команду, **Тест Sub команды**. Обратите внимание, что нажатие **команды Test Sub** ничего не делает.

## <a name="add-a-command"></a>Добавление команды

1. Откройте *TestCommand.cs* и добавьте следующий идентификатор команды после существующего идентификатора команды.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Добавьте подкоманду. Найдите конструктора команд. Добавьте следующие строки сразу `AddCommand` после вызова в метод.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Обработчик `SubItemCallback` команды будет определен позже. Конструктор должен теперь выглядеть следующим образом:

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
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Добавьте `SubItemCallback()`. Это метод, который называется при нажатии новой команды в подменю.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
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

4. Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен появиться.

5. В меню **TestMenu** щелкните **Sub Menu,** а затем нажмите **Команду Test Sub.** Окно сообщений должно отображаться и отображать текст", "Тест-команда Внутри TestCommand.SubItemCallback()".

## <a name="see-also"></a>См. также

- [Добавьте меню в панель меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
