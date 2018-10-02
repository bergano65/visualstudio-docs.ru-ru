---
title: Изменение внешнего вида команды | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d707451b71efdd41a470c2e1e54353e2fdfe4f01
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572293"
---
# <a name="changing-the-appearance-of-a-command"></a>Изменение внешнего вида команды
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [изменение внешнего вида команды](https://docs.microsoft.com/visualstudio/extensibility/changing-the-appearance-of-a-command).  
  
Пользователю можно предоставить отзыв, изменение внешнего вида команды. Например вы можете команду, чтобы выглядеть иначе, когда она недоступна. Можно сделать команды доступными или недоступными, скрыть или отобразить их, или проверить или снять их флажки в меню.  
  
 Чтобы изменить внешний вид команды, выполните одно из следующих действий.  
  
-   Укажите соответствующие флаги в определении команды в файл таблицы команд.  
  
-   Используйте <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> службы.  
  
-   Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс и изменять объекты raw-команда.  
  
 Ниже показано, как найти и обновить внешний вид команды с помощью Managed Package Framework (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Для изменения внешнего вида команды меню  
  
1.  Следуйте инструкциям в [изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md) для создания элемента меню с именем `New Text`.  
  
2.  В файле ChangeMenuText.cs, добавьте следующий оператор using:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  В файле ChangeMenuTextPackageGuids.cs добавьте следующую строку:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  В файле ChangeMenuText.cs замените код метода ShowMessageBox следующим:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Получить команду, которая требуется обновить из <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> и задайте соответствующие свойства объекта команды. Например следующий метод делает указанной команды VSPackage набор команд доступна или недоступна. Следующий код делает меню под названием `New Text` недоступным после он был выполнен щелчок.  
  
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
  
7.  На **средства** меню, щелкните **вызова ChangeMenuText** команды. На этом этапе является имя команды **вызова ChangeMenuText**, поэтому обработчик команд не вызывает ChangeMyCommand().  
  
8.  На **средства** меню, теперь вы увидите **новый текст**. Нажмите кнопку **новый текст**. Теперь нужно запретить команду.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

