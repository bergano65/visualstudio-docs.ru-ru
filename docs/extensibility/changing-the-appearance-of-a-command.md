---
title: Изменение внешнего вида командования (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739860"
---
# <a name="change-the-appearance-of-a-command"></a>Изменение внешнего вида команды
Вы можете предоставить обратную связь пользователю, изменив внешний вид команды. Например, можно пожелать, чтобы команда выглядела по-другому, когда она недоступна. Вы можете сделать команды доступными или недоступными, скрыть или показать их, проверить или отменить их в меню.

Чтобы изменить внешний вид команды, выполните одно из следующих действий:

- Укажите соответствующие флаги в определении команды в файле таблицы команд.

- Воспользуйтесь услугой. <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>

- Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса и изменение необработанных командных объектов.

  Следующие шаги показывают, как найти и обновить внешний вид команды с помощью Рамочной системы управляемого пакета (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Изменить внешний вид команды меню

1. Следуйте инструкциям в [Изменить текст команды меню](../extensibility/changing-the-text-of-a-menu-command.md) для `New Text`создания элемента меню под названием .

2. В *ChangeMenuText.cs* файле добавьте следующее заявление с помощью:

    ```csharp
    using System.Security.Permissions;
    ```

3. В *файле ChangeMenuTextPackageGuids.cs* добавьте следующую строку:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. В *ChangeMenuText.cs* файле замените код в методе ShowMessageBox следующим:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Получите команду, которую требуется обновить с <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> объекта, а затем установите соответствующие свойства на объекте команды. Например, следующий метод делает указанную команду из набора команд VSPackage доступной или недоступной. Следующий код делает элемент `New Text` меню названным недоступным после нажатия.

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
        return cmdUpdated;
    }
    ```

6. Выполните сборку решения и запустите отладку. Экспериментальный экземпляр Visual Studio должен появиться.

7. В меню **«Инструменты»** щелкните команду **ChangeMenuText.** На данный момент имя команды **— вызов ChangeMenuText,** поэтому обработчик команды не вызывает **ChangeMyCommand()**.

8. В меню **Tools** теперь вы должны увидеть **новый текст**. Нажмите **новый текст**. Теперь команда должна быть поседенной.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
- [Как VSPackages добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
- [Командный стол Visual Studio (. Vsct) Файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
