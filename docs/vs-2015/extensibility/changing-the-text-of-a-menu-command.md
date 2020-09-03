---
title: Изменение текста команды меню | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8fd3fc01a5dd3e10e633b876b719695d6b26c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184497"
---
# <a name="changing-the-text-of-a-menu-command"></a>Изменение текста команды меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В следующих шагах показано, как изменить текстовую метку команды меню с помощью <xref:System.ComponentModel.Design.IMenuCommandService> службы.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Изменение метки команды меню с помощью Именукоммандсервице  
  
1. Создайте проект VSIX с именем `MenuText` с помощью команды меню с именем **чанжеменутекст**. Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. В файле встк добавьте `TextChanges` флаг в команду меню, как показано в следующем примере.  
  
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
  
3. В файле ChangeMenuText.cs Создайте обработчик событий, который будет вызываться перед отображением команды меню.  
  
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
  
     Вы также можете обновить состояние команды меню в этом методе, изменив <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> свойства, и <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> объекта.  
  
4. В конструкторе Чанжеменутекст замените исходную инициализацию команды и код размещения кодом, который создает <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (а не `MenuCommand` ), который представляет команду меню, добавляет <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчик событий и передает команду меню в службу команд меню.  
  
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
  
5. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
6. В меню **Сервис** должна отобразиться команда с именем **Invoke чанжеменутекст**.  
  
7. Щелкните команду. Должно отобразиться окно с сообщением о том, что Менуитемкаллбакк был вызван. Когда вы откроете окно сообщения, вы увидите, что имя команды в меню Сервис теперь является **новым текстом**.
