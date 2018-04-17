---
title: Изменение текста команды меню | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 717e360e08cbdfee23221b9384a5574530f92e23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="changing-the-text-of-a-menu-command"></a>Изменение текста команды меню
Ниже показано, как изменить текстовую подпись команды меню с помощью <xref:System.ComponentModel.Design.IMenuCommandService> службы.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Изменение метки меню команд с IMenuCommandService  
  
1.  Создайте проект VSIX с именем `MenuText` с помощью команды меню с именем **ChangeMenuText**. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Добавьте в файл .vstc `TextChanges` флаг команды меню, как показано в следующем примере.  
  
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
  
3.  В файле ChangeMenuText.cs создайте обработчик событий, который будет вызываться перед отображением команды меню.  
  
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
  
     Состояние команды меню в этот метод также можно обновить, изменив <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, и <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> свойства <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> объекта.  
  
4.  В конструкторе ChangeMenuText замените код, который создает исходный код инициализации и размещения команды <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (а не `MenuCommand`), представляющее команду меню, добавляет <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчик событий и предоставляет меню Команда службу команд меню.  
  
     Вот, оно должно иметь вид:  
  
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
  
5.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
6.  На **средства** меню появится команда **ChangeMenuText вызова**.  
  
7.  Выберите команду. Вы увидите поле сообщение объявляет о том, что MenuItemCallback был вызван. После закрытия окна сообщения, вы увидите, что теперь имя команды меню "Сервис" — **новый текст**.
