---
title: Изменение внешнего вида команды | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a19793f16991bc61636a929822757823728a926
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099087"
---
# <a name="changing-the-appearance-of-a-command"></a>Изменение внешнего вида команды
Пользователю можно отправить отзыв, изменение внешнего вида команды. Например может потребоваться команды выглядят иначе, когда она недоступна. Можно сделать команды доступна или недоступна, скрыть или отобразить их, или проверьте или снимите флажки возле них в меню.  
  
 Чтобы изменить внешний вид команды, выполните одно из следующих действий.  
  
-   Укажите соответствующие флаги в определении команду в файл таблицы команд.  
  
-   Используйте <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> службы.  
  
-   Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс и изменять объекты необработанных команд.  
  
 Ниже показано, как найти и обновить внешний вид команды с помощью Managed Package Framework (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Чтобы изменить внешний вид команды меню  
  
1.  Следуйте инструкциям в [изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md) для создания пункта меню с именем `New Text`.  
  
2.  В файле ChangeMenuText.cs добавьте следующие инструкции с помощью:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  В файле ChangeMenuTextPackageGuids.cs добавьте следующую строку:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  В файле ChangeMenuText.cs замените код в методе ShowMessageBox следующее:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Получить команду, необходимо выполнить обновление из <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> объекта и задайте соответствующие свойства в объекте command. Например следующий метод делает указанную команду из команды VSPackage задать доступна или недоступна. Следующий код делает меню под названием `New Text` недоступна после была нажата.  
  
    ```csharp  
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
  
6.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
7.  На **средства** меню, нажмите кнопку **ChangeMenuText вызова** команды. На этом этапе имя команды — **ChangeMenuText вызова**, поэтому обработчик команд не вызывает ChangeMyCommand().  
  
8.  На **средства** меню, вы увидите **новый текст**. Нажмите кнопку **новый текст**. Команда теперь должны быть недоступны.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)