---
title: Реализация команды | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a208fabd3d205793763698cde0f6fe367c7bb8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195063"
---
# <a name="command-implementation"></a>Реализация команд
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Для реализации команды в VSPackage необходимо выполнить следующие задачи.  
  
1. В vsct-файле Настройте группу команд и добавьте в нее команду. Дополнительные сведения см. в разделе [Командная таблица Visual Studio (. Vsct) файлы](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
  
2. Зарегистрируйте команду в Visual Studio.  
  
3. Реализуйте команду.  
  
   В следующих разделах объясняется, как регистрировать и реализовывать команды.  
  
## <a name="registering-commands-with-visual-studio"></a>Регистрация команд в Visual Studio  
 Если команда отображается в меню, необходимо добавить в <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage и использовать в качестве значения имя меню или его идентификатор ресурса.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Кроме того, необходимо зарегистрировать команду с помощью <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . Эту службу можно получить с помощью метода, <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Если пакет VSPackage является производным от <xref:Microsoft.VisualStudio.Shell.Package> .  
  
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
  
## <a name="implementing-commands"></a>Реализация команд  
 Существует несколько способов реализации команд. Если вам нужна статическая команда меню, которая является командой, которая всегда выглядит одинаковым образом и в том же меню, создайте команду, используя, <xref:System.ComponentModel.Design.MenuCommand> как показано в примерах из предыдущего раздела. Чтобы создать статическую команду, необходимо предоставить обработчик событий, отвечающий за выполнение команды. Так как команда всегда включена и видима, нет необходимости предоставлять свое состояние Visual Studio. Если вы хотите изменить состояние команды в зависимости от определенных условий, можно создать команду как экземпляр <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> класса и в своем конструкторе предоставить обработчик событий для выполнения команды, а обработчик состояния запроса — для уведомления Visual Studio об изменении состояния команды. Также можно реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> как часть класса команд или, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Если вы предоставляете команду в составе проекта. У двух интерфейсов и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> класса есть методы, которые уведомляют Visual Studio об изменении состояния команды, а также другие методы, которые обеспечивают выполнение команды.  
  
 При добавлении команды в службу команд она становится одной из цепочки команд. При реализации уведомлений о состоянии и методов выполнения для команды следует принять во внимание только для этой конкретной команды и передавать все остальные варианты в другие команды в цепочке. Если не передать команду в (обычно путем возврата <xref:Microsoft.VisualStudio.OLE.Interop.Constants> ), Visual Studio может работать неправильно.  
  
## <a name="query-status-methods"></a>Методы состояния запроса  
 При реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> метода проверьте идентификатор GUID набора команд, к которому принадлежит команда, и идентификатор команды. Соблюдайте следующие правила.  
  
- Если идентификатор GUID не распознан, ваша реализация любого метода должна возвращать значение <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Если ваша реализация любого из методов распознает GUID, но не реализовал команду, метод должен вернуть значение <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Если ваша реализация любого из методов распознает и идентификатор GUID, и команду, то метод должен задать поле Command-flags каждой команды (в `prgCmds` параметре), используя следующие флаги:  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Если команда поддерживается.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> значение, если команда не должна быть видимой.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> значение, если команда включена и по-видимому установлен.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Если команда включена.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> значение, если команда должна быть скрыта, если она отображается в контекстном меню.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Если команда является контроллером меню и не включена, но список раскрывающихся меню не пуст и по-прежнему доступен. (Этот флаг редко используется.)  
  
- Если команда была определена в файле. vsct с `TextChanges` флагом, задайте следующие параметры:  
  
  - Присвойте `rgwz` элементу `pCmdText` параметра новый текст команды.  
  
  - Задайте `cwActual` `pCmdText` для элемента параметра размер строки команды.  
  
  Кроме того, убедитесь, что текущий контекст не является функцией автоматизации, если только команда не предназначена специально для работы с функциями автоматизации.  
  
  Чтобы указать, что вы поддерживаете определенную команду, возвратите <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Для всех остальных команд возвращается <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
  В следующем примере метод запроса состояния сначала проверяет, что контекст не является функцией автоматизации, а затем находит правильный идентификатор GUID набора команд и идентификатор команды. Сама команда настроена как включенная и поддерживаемая. Другие команды не поддерживаются.  
  
```  
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
 Реализация метода Execute похожа на реализацию метода состояния запроса. Во-первых, убедитесь, что контекст не является функцией автоматизации. Затем проверьте идентификатор GUID и идентификатор команды. Если идентификатор GUID или идентификатора команды не распознан, возвращается значение <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
 Чтобы обработать команду, выполните ее и вернитесь <xref:Microsoft.VisualStudio.VSConstants.S_OK> в случае успешности выполнения. Ваша команда отвечает за обнаружение и уведомление об ошибках; Поэтому при сбое выполнения верните код ошибки. В следующем примере показано, как должен быть реализован метод выполнения.  
  
```  
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
  
## <a name="see-also"></a>См. также:  
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
