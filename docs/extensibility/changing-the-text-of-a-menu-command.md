---
title: Изменение текста команды меню (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739842"
---
# <a name="change-the-text-of-a-menu-command"></a>Изменить текст команды меню
Следующие шаги показывают, как изменить текстовую метку команды меню с помощью службы. <xref:System.ComponentModel.Design.IMenuCommandService>

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Изменение метки команды меню с помощью IMenuCommandService

1. Создайте проект VSIX с `MenuText` командой меню под названием **ChangeMenuText**. Для получения дополнительной информации [см. Создать расширение с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. В файле *«vsct»* добавьте `TextChanges` флаг в команду меню, как показано в следующем примере.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. В *ChangeMenuText.cs* файле создайте обработчик событий, который будет вызываться до отображения команды меню.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    Вы также можете обновить состояние команды меню в <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>этом <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>методе, изменив, и <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> свойства на объекте. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>

4. В конструкторе ChangeMenuText замените исходный код инициализации <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> и размещения `MenuCommand`команды кодом, который <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> создает (а не) команду меню, добавляет обработчик событий и дает команду меню службе команды меню.

    Вот как это должно выглядеть:

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр Visual Studio.

6. В меню **«Инструменты»** вы должны увидеть команду под названием **Invoke ChangeMenuText.**

7. Нажмите на команду. Вы должны увидеть окно сообщения объявляет, что **MenuItemCallback** был вызван. При отклонении окна сообщений следует видеть, что название команды в меню «Инструменты» теперь является **новым текстом.**
