---
title: Команда реализации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61f35521271df7d3f34e5f10ebf40d502c0f8596
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089757"
---
# <a name="command-implementation"></a>Реализация команды
Чтобы реализовать команду в VSPackage, необходимо выполнить следующие задачи:

1. В *.vsct* файл, настройте группу команд и добавьте к нему команду. Дополнительные сведения см. в разделе [Visual Studio командные table (.vsct) файлы](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

2. Регистрация команды с помощью Visual Studio.

3. Реализуйте команду.

Способ регистрации и реализовывать команды в следующих разделах.

## <a name="register-commands-with-visual-studio"></a>Регистрация команд с помощью Visual Studio
 Если вашей команды — это меню, необходимо добавить <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> в свой пакет VSPackage и использовать как значение имени меню или его идентификатор ресурса.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Кроме того, необходимо зарегистрировать командой <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Эту службу можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод, если VSPackage является производным от <xref:Microsoft.VisualStudio.Shell.Package>.

```
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
if ( null != mcs )
{
    // Create the command for the menu item.
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );
    mcs.AddCommand( menuItem );
}

```

## <a name="implement-commands"></a>Реализация команд
 Существует ряд способов реализации команд. Команду статического меню, что является команда, которая всегда отображается одинаково, так и в том же меню, создать команду с помощью <xref:System.ComponentModel.Design.MenuCommand> как показано в примерах в предыдущем разделе. Чтобы создать статических команд, необходимо предоставить обработчик событий, который отвечает за выполнение команды. Так как команда всегда включена и отображается, у вас нет для предоставления его состояние в Visual Studio. Если вы хотите изменить состояние команды в зависимости от определенных условий, можно создать команду как экземпляр <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> класса и в его конструктор предоставить обработчик событий, чтобы выполнить команду и `QueryStatus` обработчик для уведомления Visual Studio при изменении состояния команды. Вы также можете реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> как можно реализовать класс команд или <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Если команды предоставляется как часть проекта. Эти два интерфейса и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> класса все имеют методы, которые уведомления Visual Studio об изменении состояния команды и другие методы, которые обеспечивают выполнение команды.

 При добавлении команды службу команд, он становится одним из цепочки команд. При реализации состояния уведомления и выполнение методов для команды, будьте внимательны обеспечить только для этой конкретной командой и для передачи всех остальных случаях на другие команды в цепочке. Если не удалось передать команду (как правило, возвращая <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), Visual Studio может перестать работать должным образом.

## <a name="querystatus-methods"></a>Методы QueryStatus
 Если вы реализуете либо <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> метод, проверка идентификатора GUID набора команд, которому принадлежит команды и идентификатор команды. Соблюдайте следующие правила.

- Если идентификатор GUID не распознан, реализации любого из этих методов должны возвращать <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.

- Если реализации любого из этих методов распознает идентификатор GUID, но команда не реализована, то этот метод должен возвращать <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

- Если реализации любого из этих методов распознает как идентификатор GUID, так и команды, то метод должен настроить поле флаги команды каждой из команд (в `prgCmds` параметра) с помощью следующих <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> флаги:

    - `OLECMDF_SUPPORTED`: Команда поддерживается.

    - `OLECMDF_INVISIBLE`: Команда не должны быть видимыми.

    - `OLECMDF_LATCHED`: Команда включена и появляется указатель были проверены.

    - `OLECMDF_ENABLED`: Команда включена.

    - `OLECMDF_DEFHIDEONCTXTMENU`: Команда должна быть скрыта, если он отображается в контекстном меню.

    - `OLECMDF_NINCHED`: Команда выполняется в контроллере меню и не включен, но его раскрывающееся меню списка не является пустым и по-прежнему доступна. (Этот флаг используется редко.)

- Если команда было определено в *.vsct* файл с `TextChanges` флаг, задайте следующие параметры:

    - Задайте `rgwz` элемент `pCmdText` параметр новый текст команды.

    - Задайте `cwActual` элемент `pCmdText` размер командной строки.

Кроме того убедитесь, что текущий контекст не функцию автоматизации, если команда специально предназначен для обработки функций автоматизации.

Чтобы указать, что вы поддерживают определенной команды, вернуть <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Для всех остальных команды возвращают <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

В следующем примере `QueryStatus` метод сначала гарантирует, что контекст не является функцией службы автоматизации, а затем находит правильный идентификатор GUID набора команд и идентификатор команды. Включены также поддерживаться присваивается в саму команду. Другие команды не поддерживаются.

```csharp
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)
        {
            // make the Right command visible
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;
                return VSConstants.S_OK;
            }
        }
        return Constants.OLECMDERR_E_NOTSUPPORTED;
    }
}
```

## <a name="execution-methods"></a>Методы выполнения
 Реализация `Exec` метод похож на реализацию `QueryStatus` метод. Во-первых убедитесь, что контекст не функцию автоматизации. Проверьте идентификатор GUID и идентификатор команды. Если идентификатор GUID или Неизвестный идентификатор команды, возвращается <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

 Для обработки команды, выполнить его и возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK> успешное завершение выполнения. Команда отвечает за обнаружение ошибок и уведомления; Таким образом возвращают код ошибки, если происходит сбой выполнения. В следующем примере показано, как должны быть реализованы в метод выполнения.

```csharp
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)
        {
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                //execute the command
                return VSConstants.S_OK;
            }
        }
    }
    return Constants.OLECMDERR_E_NOTSUPPORTED;
}
```

## <a name="see-also"></a>См. также

- [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)