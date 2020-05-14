---
title: Добавление контроллера меню в панель инструментов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4dcb9e51f6633476a8f0eadea30da513e5ef760
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740329"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Добавление контроллера меню в панель инструментов
Это пошаговое решение построено на [панели инструментов в пошаговую](../extensibility/adding-a-toolbar-to-a-tool-window.md) панель окна инструмента и показывает, как добавить контроллер меню в панель инструментов. Действия, показанные здесь, также могут быть применены к панели инструментов, которая создается в [пошаговом](../extensibility/adding-a-toolbar.md) слове панели инструментов.

Контроллер меню — это элемент управления разделением. В левой части контроллера меню отображается последняя используемая команда, и вы можете запустить ее, нажав на нее. Правая сторона контроллера меню — стрелка, которая при нажатии открывает список дополнительных команд. При нажатии на команду в списке команда выполняется, и она заменяет команду на левой стороне контроллера меню. Таким образом, контроллер меню работает как кнопка команды, которая всегда показывает последнюю используемую команду из списка.

Контроллеры меню могут отображаться в меню, но чаще всего они используются на панели инструментов.

## <a name="prerequisites"></a>Предварительные требования
Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-menu-controller"></a>Создание контроллера меню

1. Следуйте процедурам, описанным в [добавлении панели инструментов в окно инструмента,](../extensibility/adding-a-toolbar-to-a-tool-window.md) чтобы создать окно инструмента с панелью инструментов.

2. В *TWTestCommandPackage.vsct,* перейдите в раздел Символы. В элементе GuidSymbol под названием **guidTWTestCommandPackageDSet**объявите контроллер меню, группу контроллера меню и три элемента меню.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. В разделе Меню после последней записи меню определите контроллер меню как меню.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    `TextChanges` Флаги `TextIsAnchorCommand` и флаги должны быть включены, чтобы контроллер меню отражал последнюю выбранную команду.

4. В разделе Группы после последней записи в группе добавьте группу контроллеров меню.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Установив контроллер меню в качестве родительского элемента, все команды, помещенные в эту группу, отображаются в контроллере меню. Атрибут `priority` опущен, что устанавливает его на значение по умолчанию 0, потому что это единственная группа в контроллере меню.

5. В разделе Кнопки после последней записи кнопки добавьте элемент кнопки для каждого из элементов меню.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. На этом этапе вы можете посмотреть на контроллер меню. Выполните сборку решения и запустите отладку. Вы должны увидеть экспериментальный экземпляр.

   1. В **представлении / Другое** меню Windows, open **Test ToolWindow**.

   2. Контроллер меню отображается на панели инструментов в окне инструмента.

   3. Нажмите на стрелку на правой стороне контроллера меню, чтобы увидеть три возможные команды.

      Обратите внимание, что при нажатии на команду название контроллера меню изменяется для отображения этой команды. В следующем разделе мы добавим код для активации этих команд.

## <a name="implement-the-menu-controller-commands"></a>Реализация команд контроллера меню

1. В *TWTestCommandPackageGuids.cs*добавьте иные иудеи команд для трех пунктов меню после существующих идонов команд.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. В *TWTestCommand.cs*добавьте следующий код `TWTestCommand` в верхней части класса.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. В конструкторе TWTestCommand после последнего `AddCommand` вызова метода добавьте код для маршрутизации для каждой команды через одни и те же обработчики.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Добавьте обработчик событий в класс **TWTestCommand,** чтобы отметить выбранную команду проверенной.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Добавьте обработчик событий, который отображает MessageBox, когда пользователь выбирает команду на контроллере меню:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Тестирование контроллера меню

1. Выполните сборку решения и запустите отладку. Вы должны увидеть экспериментальный экземпляр.

2. Откройте **тестовый toolWindow** в **представлении / Другое** меню Windows.

    Контроллер меню отображается в панели инструментов в окне инструмента и отображает **MC Пункт 1**.

3. Нажмите кнопку контроллера меню слева от стрелки.

    Вы должны увидеть три элемента, первый из которых выбран и имеет поле выделения вокруг своего значка. Нажмите **MC Пункт 3**.

    Появляется диалоговое окно с выбранным **вами элементом 3 контроллера меню.** Обратите внимание, что сообщение соответствует тексту на кнопке контроллера меню. Кнопка контроллера меню теперь отображает **MC Пункт 3**.

## <a name="see-also"></a>См. также
- [Добавление панели инструментов в окно инструмента](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)
