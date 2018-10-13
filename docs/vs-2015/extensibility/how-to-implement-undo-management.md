---
title: 'Практическое: реализовать механизмы управления отменой | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72355b396dc88fc02c1ccdfb4f3a2ed4afe66467
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246290"
---
# <a name="how-to-implement-undo-management"></a>Практическое: реализовать механизмы управления отменой
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Основным интерфейсом для управления отката является <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, который реализуется с помощью среды. Для поддержки управления отменой, реализации единиц отката отдельные (то есть <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, который может содержать несколько отдельных шагов.  
  
 Как реализовать механизмы управления отменой зависит от ли ваш редактор поддерживает несколько представлений или нет. В следующих разделах описаны процедуры для каждой реализации.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Случаи, когда редактор поддерживает одно представление  
 В этом случае редактор не поддерживает несколько представлений. Имеется только один редактор и один документ, и они поддерживают отмены. Используйте следующую процедуру для реализации управления отката.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Для поддержки управления отменой для редактора одним представлением  
  
1.  Вызовите `QueryInterface` на `IServiceProvider` интерфейса на фрейм окна для `IOleUndoManager`, из объекта представления документа, чтобы открыть диспетчер отмены (`IID_IOLEUndoManager`).  
  
2.  При размещении представления в рамку окна, он получает указатель сайта, который он может использовать для вызова `QueryInterface` для `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Случаи, когда редактор поддерживает несколько представлений  
 Если у вас есть Разделение документа и представления, то есть обычно один диспетчер отмены связан сам документ. Все блоки отмены помещаются на один диспетчер отмены связанный с объектом данных документа.  
  
 Вместо представления запрашивая диспетчер отмены, из которых имеется один для каждого представления, объект данных документа, вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> для создания экземпляра диспетчер отмены, указав идентификатор класса CLSID_OLEUndoManager. Идентификатор класса определяется в файле OCUNDOID.h.  
  
 При использовании <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> для создания вашего собственного экземпляра диспетчер отмены, используйте следующую процедуру, чтобы подключить ваш Диспетчер отката в среду.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Чтобы подключить ваш Диспетчер отката в среду  
  
1.  Вызовите `QueryInterface` на объект, возвращенный из <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> для `IID_IOleUndoManager`. Указатель на Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Вызовите `QueryInterface` на `IOleUndoManager` для `IID_IOleCommandTarget`. Указатель на Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Ретрансляции вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> вызывает сохраненную `IOleCommandTarget` интерфейса для следующих команд StandardCommandSet97:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Вызовите `QueryInterface` на `IOleUndoManager` для `IID_IVsChangeTrackingUndoManager`. Указатель на Store <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Использование указателя для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> для вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> методы.  
  
5.  Вызовите `QueryInterface` на `IOleUndoManager` для `IID_IVsLinkCapableUndoManager`.  
  
6.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> в документе, которые также реализуют <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> интерфейс. При закрытии документа, вызвать `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  При закрытии документа, вызвать `QueryInterface` на ваш диспетчер отмены для `IID_IVsLifetimeControlledObject`.  
  
8.  Вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. При внесении изменений в документ, вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> в диспетчере с `OleUndoUnit` класса. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Метод сохраняет ссылку на объект, обычно Вы освободите его непосредственно после <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 `OleUndoManager` Класс представляет экземпляр стека одной операции отката. Таким образом только один объект диспетчера отмены на сущность данных отслеживается для отмены или повтора.  
  
> [!NOTE]
>  Объект диспетчера отмены широко применяется в текстовом редакторе, это общий компонент, который не имеет определенного поддержки для текстового редактора. Если вы хотите поддерживать многоуровневые операции отмены или повтора, для этого можно использовать этот объект.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Практическое руководство. Очистка стека отмены](../extensibility/how-to-clear-the-undo-stack.md)

