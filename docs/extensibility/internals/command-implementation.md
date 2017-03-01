---
title: "Реализация команды | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bd3c23baffe767083bc541fa9e2e8718834b3ee1
ms.lasthandoff: 02/22/2017

---
# <a name="command-implementation"></a>Реализация команды
Чтобы реализовать команду в VSPackage, необходимо выполнить следующие задачи:  
  
1.  В файле .vsct настроить группы команд и добавьте команду. Дополнительные сведения см. в разделе [таблицы команд Visual Studio (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)"  
  
2.  Регистрация команды с помощью Visual Studio.  
  
3.  Реализуйте команду.  
  
 Ниже описаны процедуры для регистрации и реализации команд.  
  
## <a name="registering-commands-with-visual-studio"></a>Регистрация команды в Visual Studio  
 Если команда будет отображаться в меню, необходимо добавить <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>VSPackage, и используйте в качестве значения имя меню или его идентификатор ресурса.</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Кроме того необходимо зарегистрировать команда <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Эту службу можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>метода VSPackage, производным от <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
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
  
## <a name="implementing-commands"></a>Реализация команды  
 Существует несколько способов реализации команд. Команду статического меню, которая представляет команду, которая всегда отображается одинаково, так и в том же меню, создать команду с помощью <xref:System.ComponentModel.Design.MenuCommand>как показано в примерах в предыдущем разделе.</xref:System.ComponentModel.Design.MenuCommand> Чтобы создать статический команду, необходимо предоставить обработчик событий, который отвечает за выполнение команды. Так как команда всегда включена и видимым, у вас для обеспечения его состояние в Visual Studio. Если вы хотите изменить состояние команды в зависимости от определенных условий, можно создать команду как экземпляр <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>класса и в его конструктор предоставить обработчик событий для выполнения команды и состояние запроса обработчику уведомления Visual Studio при изменении состояния команды.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Также можно реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>как часть класса команд или можно реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Если команду предоставляется как часть проекта.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Эти два интерфейса и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>всех классов имеют методы, уведомляющие Visual Studio об изменении состояния команды и другие методы, обеспечивающие выполнение команды.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand>  
  
 При добавлении команды службе команда становится одним из цепочки команд. При реализации уведомлений и выполнение методов состояние команды позаботиться для предоставления только для этой конкретной команды, так и для передачи всех остальных случаях на другие команды в цепочке. Если вам не удается передать команду (как правило, возвращая <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio может перестать работать правильно.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
## <a name="query-status-methods"></a>Методы запроса состояния  
 Если вы реализуете либо <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>метод или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>метод, проверьте идентификатор GUID набора команд, которому принадлежит команды и идентификатор команды.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Соблюдайте следующие правила.  
  
-   Если идентификатор GUID не распознан, реализации метод должен возвращать <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   При реализации любого из методов распознает GUID, но на самом деле не реализован команды, метод должен вернуть <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   Если реализации одного из методов распознает GUID и команды, то метод должен задать в поле Команда флаги каждой из команд (в `prgCmds` параметров), используя следующие флаги:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда поддерживается.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда не должны быть видимыми.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда включена и кажется были проверены.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда включена.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда должен быть скрыт, он отображается в контекстном меню.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда является контроллером меню не включен, а раскрывающееся меню список не пуст и по-прежнему доступен.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> (Этот флаг используется редко.)  
  
-   Если команда был определен в файле .vsct `TextChanges` флаг, установите следующие параметры:  
  
    -   Задайте `rgwz` элемент `pCmdText` параметра новый текст команды.  
  
    -   Задайте `cwActual` элемент `pCmdText` параметра размер командной строки.  
  
 Также убедитесь, что текущий контекст не является функцией автоматизации Если команда специально предназначены для обработки функций автоматизации.  
  
 Для указания, что вы поддерживаете определенной команды, возвращаемого <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> Все другие команды возвращают <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 В следующем примере метод состояние запроса сначала гарантирует, что контекст не функцию автоматизации, а затем находит правильный набор команд GUID и идентификатор команды. Имеет значение сама команда быть включена и поддерживается. Другие команды не поддерживаются.  
  
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
  
## <a name="execution-methods"></a>Выполнение методов  
 Реализация метода execute напоминает реализацию метода состояние запроса. Во-первых убедитесь, что контекст не функцию автоматизации. Проверьте идентификатор GUID и идентификатор команды. Если идентификатор GUID или команда не опознан код возврата <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 Для обработки команды, выполнять его и возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK>Если выполнение завершится успешно.</xref:Microsoft.VisualStudio.VSConstants.S_OK> Команда отвечает за обнаружение ошибок и уведомления; Таким образом возвращается код ошибки, если происходит сбой выполнения. В следующем примере показано, как метод выполнения должен быть реализован.  
  
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
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
