---
title: "Изменение текста команды меню | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Изменение текста меню"
  - "текст меню"
  - "команды, изменение текста"
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Изменение текста команды меню
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ниже показано, как изменить текстовую метку для команды меню с помощью <xref:System.ComponentModel.Design.IMenuCommandService> службы.  
  
## Изменение метки команды меню с IMenuCommandService  
  
1.  Создайте проект VSIX с именем `MenuText` с командой меню с именем **ChangeMenuText**. Для получения дополнительной информации см. [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
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
  
    ```c#  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
                    }  
    }  
    ```  
  
     Можно также обновить состояние команды меню в этом методе, изменив <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, и <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> Свойства <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> объекта.  
  
4.  В конструкторе ChangeMenuText замените код, который создает исходный код инициализации и размещения команды <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> \(а не `MenuCommand`\), которые представляет команды меню, добавляет <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчик событий и предоставляет команду меню, чтобы служба команд меню.  
  
     Вот, что оно должно выглядеть.  
  
    ```c#  
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
  
6.  На **средства** меню вы должны увидеть команды с именем **вызова ChangeMenuText**.  
  
7.  Выберите команду. Появится окно сообщения объявляет о вызов MenuItemCallback. После закрытия окна сообщения, вы увидите, что теперь имеет имя команды в меню Сервис **новый текст**.