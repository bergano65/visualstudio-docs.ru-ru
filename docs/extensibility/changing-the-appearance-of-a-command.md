---
title: "Изменение внешнего вида команды | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "команды, изменение внешнего вида"
  - "команды меню, изменение внешнего вида"
  - "Изменение внешнего вида команды меню"
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Изменение внешнего вида команды
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Пользователю можно отправить отзыв, изменив внешний вид команды. Например вы можете команду, чтобы выглядеть иначе, когда она недоступна. Можно сделать команды доступными или недоступными, скрыть или отобразить их, или проверьте или снимите соответствующий флажок в меню.  
  
 Чтобы изменить внешний вид команды, выполните одно из следующих действий:  
  
-   Укажите соответствующие флаги в определении команды в командном файле таблицы.  
  
-   Используйте <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> службы.  
  
-   Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс и изменять объекты raw\-команда.  
  
 Следующие шаги показывают, как находить и изменять внешний вид команды с помощью управляемых пакета Framework \(MPF\).  
  
### Чтобы изменить внешний вид команды меню  
  
1.  Следуйте инструкциям в [Изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md) для создания элемента меню с именем `New Text`.  
  
2.  В файле ChangeMenuText.cs добавьте следующий оператор using:  
  
    ```c#  
    using System.Security.Permissions;  
    ```  
  
3.  В файле ChangeMenuTextPackageGuids.cs добавьте следующую строку:  
  
    ```c#  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  В файле ChangeMenuText.cs замените код в методе ShowMessageBox следующее:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Получить команду, необходимо выполнить обновление из <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> и задайте соответствующие свойства в объекте команды. Например следующий метод делает указанной команды VSPackage набор команд доступна или недоступна. В следующем коде выполняется меню элемент с названием `New Text` недоступной после был выполнен щелчок.  
  
    ```c#  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  Выполните сборку решения и запустите отладку. Должна появиться экспериментальном экземпляре Visual Studio.  
  
7.  На **средства** меню, щелкните **вызова ChangeMenuText** команды. На этом этапе имя команды — **вызова ChangeMenuText**, поэтому обработчик команды не вызывает ChangeMyCommand\(\).  
  
8.  На **средства** меню, вы увидите **новый текст**. Щелкните **новый текст**. Команда должна теперь серым цветом.  
  
## См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)