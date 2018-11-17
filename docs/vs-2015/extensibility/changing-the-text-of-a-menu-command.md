---
title: Изменение текста команды меню | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 52e0319edd7d8f9563998adc18e3b00f7c12713b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786474"
---
# <a name="changing-the-text-of-a-menu-command"></a>Изменение текста команды меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ниже показано, как изменить текстовую метку команды меню с помощью <xref:System.ComponentModel.Design.IMenuCommandService> службы.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Изменение метки команды меню с IMenuCommandService  
  
1.  Создайте проект VSIX с именем `MenuText` с помощью команды меню с именем **ChangeMenuText**. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Добавьте в файл .vstc, `TextChanges` флаг команды меню, как показано в следующем примере.  
  
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
  
     Можно также обновить состояние команды меню в этом методе, изменив <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, и <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> свойства <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> объекта.  
  
4.  В конструкторе ChangeMenuText замените исходный код инициализации и размещение команды код, создающий <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (а не `MenuCommand`), представляющий команду меню, добавляет <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчик событий и предоставляет меню Команда службу команд меню.  
  
     Вот, она должна выглядеть как:  
  
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
  
6.  На **средства** меню вы увидите команду с именем **вызвать ChangeMenuText**.  
  
7.  Выберите команду. Вы увидите, что был вызван MenuItemCallback сообщение Представляем поле. После закрытия окна сообщения, вы увидите, что команды в меню "Сервис" теперь называется **новый текст**.

