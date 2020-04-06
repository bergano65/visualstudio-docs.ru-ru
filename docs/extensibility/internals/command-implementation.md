---
title: Реализация командования Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709578"
---
# <a name="command-implementation"></a>Реализация командования
Для реализации команды в VSPackage необходимо выполнить следующие задачи:

1. В файле *vsct* создайте группу команд, а затем добавьте к ней команду. Для получения дополнительной информации смотрите [файлы командной таблицы Visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

2. Зарегистрируйте команду в Visual Studio.

3. Реализация команды.

В следующих разделах объясняется, как зарегистрировать и реализовать команды.

## <a name="register-commands-with-visual-studio"></a>Регистрация команд с Visual Studio
 Если ваша команда должна появиться в меню, необходимо добавить его <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> в VSPackage и использовать в качестве значения либо название меню, либо идентификатор ресурса.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Кроме того, необходимо зарегистрировать команду <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>с помощью . Вы можете получить эту <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> услугу, используя метод, <xref:Microsoft.VisualStudio.Shell.Package>если ваш VSPackage является производным от .

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
 Существует несколько способов реализации команд. Если требуется статический элемент команды меню, которая представляет собой команду, которая всегда отображается одинаково и в одном и том же меню, создайте команду, используя, <xref:System.ComponentModel.Design.MenuCommand> как показано в примерах предыдущего раздела. Чтобы создать статическую команду, необходимо предоставить обработчик событий, который отвечает за выполнение команды. Поскольку команда всегда включена и видна, вам не нужно предоставлять ее статус Visual Studio. Если требуется изменить статус команды в зависимости от определенных условий, можно <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> создать команду как экземпляр класса и в своем конструкторе предоставить обработчику событий для выполнения команды и обработчику `QueryStatus` уведомить Visual Studio при изменении статуса команды. Вы также <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> можете реализовать как часть командного <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> класса или, вы можете реализовать, если вы предоставляете команду в рамках проекта. Все эти два <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> интерфейса и класс имеют методы, которые уведомляют Visual Studio об изменении статуса команды, и другие методы, обеспечивающие выполнение команды.

 Когда команда добавляется в командную службу, она становится одной из цепочек команд. При реализации методов уведомления о статусе и выполнения для команды позаботьтесь о том, чтобы обеспечить только эту конкретную команду и передать все остальные кейсы другим командам в цепочке. Если вы не сможете передать команду <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>(обычно путем возвращения), Visual Studio может перестать работать должным образом.

## <a name="querystatus-methods"></a>Методы queryStatus
 Если вы реализуете <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> метод, проверьте GUID набора команд, к которому принадлежит команда, и идентификатор команды. Соблюдайте следующие правила.

- Если GUID не распознается, ваша реализация <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>любого из методов должна вернуться.

- Если реализация любого метода распознает GUID, но не реализовала <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>команду, то метод должен вернуться.

- Если реализация любого метода распознает как GUID, так и команду, то метод должен `prgCmds` установить поле командных флагов каждой команды (в параметре) с помощью следующих <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> флагов:

  - `OLECMDF_SUPPORTED`: Команда поддерживается.

  - `OLECMDF_INVISIBLE`: Команда не должна быть видимой.

  - `OLECMDF_LATCHED`: Команда переключается и, кажется, была проверена.

  - `OLECMDF_ENABLED`: Включена команда.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Команда должна быть скрыта, если она отображается в меню ярлыка.

  - `OLECMDF_NINCHED`: Команда является контроллером меню и не включена, но ее список выпадающих меню не пуст и по-прежнему доступен. (Этот флаг используется редко.)

- Если команда была определена в файле `TextChanges` *.vsct* с флагом, установите следующие параметры:

  - Установите `rgwz` элемент `pCmdText` параметра в новый текст команды.

  - Установите `cwActual` элемент `pCmdText` параметра в размер строки команды.

Кроме того, убедитесь, что текущий контекст не является функцией автоматизации, если только ваша команда специально предназначена для обработки функций автоматизации.

Чтобы указать, что вы <xref:Microsoft.VisualStudio.VSConstants.S_OK>поддерживаете определенную команду, вернитесь . Для всех других команд, вернуться <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

В следующем примере `QueryStatus` метод сначала гарантирует, что контекст не является функцией автоматизации, а затем находит правильный набор команд GUID и идентификатор команды. Сама команда настроена на включение и поддержку. Другие команды не поддерживаются.

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
 Реализация метода `Exec` напоминает реализацию `QueryStatus` метода. Во-первых, убедитесь, что контекст не является функцией автоматизации. Затем проверьте как GUID, так и идентификатор команды. Если Идентификатор GUID или <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>командный идентификатор не распознается, вернитесь .

 Для обработки команды выполните <xref:Microsoft.VisualStudio.VSConstants.S_OK> ее и вернитесь, если выполнение удается. Ваша команда отвечает за обнаружение ошибок и уведомление; таким образом, верните код ошибки, если выполнение не выполнено. Следующий пример показывает, как должен быть реализован метод выполнения.

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

- [Как VSPackages добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
