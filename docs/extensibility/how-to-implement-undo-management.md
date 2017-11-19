---
title: "Как: реализации управления отмены | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f61ee4c561e32f17afa1b53cbf3bd3bf982feeb4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-undo-management"></a>Как: реализации управления отмены
— Это основной интерфейс для управления отмены <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, который реализуется с помощью среды. Для поддержки управления отмены, реализуйте блоков отмены отдельные (то есть <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, которое может содержать несколько отдельных шагов.  
  
 Реализация управления отмены зависит от того, поддерживает ли ваш редактор несколько представлений или нет. В следующих разделах описаны процедуры для каждой реализации.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Случаи, когда редактор поддерживает одно представление  
 В этом сценарии редактор не поддерживает несколько представлений. Имеется только один редактора и один документ и поддерживают отмены. Используйте следующую процедуру для реализации управления отмены.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Для поддержки отмены управления для представления одного редактора  
  
1.  Вызовите `QueryInterface` на `IServiceProvider` интерфейса на фрейм окна `IOleUndoManager`, из объекта представления документа для доступа к диспетчеру отмены (`IID_IOLEUndoManager`).  
  
2.  При размещении в рамки окна представления, он получает указатель сайта, который используется для вызова `QueryInterface` для `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Случаи, когда редактор поддерживает несколько представлений  
 При наличии Разделение документа и представления нет диспетчер обычно один отмены, связанный с самого документа. Все блоки отмены помещаются в диспетчер один отмены, связанный с объектом данных документа.  
  
 Вместо запрос представления диспетчер отмены, из которых имеется один для всех представлений данных документа объекта вызовы <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> Чтобы создать диспетчер отмены, указав идентификатора класса CLSID_OLEUndoManager. Идентификатор класса определена в файле OCUNDOID.h.  
  
 При использовании <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> для создания собственного экземпляра диспетчер отмены, используйте следующую процедуру для подключения вашего диспетчер отмены в среду.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Для подключения к диспетчер отмены в среду  
  
1.  Вызовите `QueryInterface` на объект, возвращаемый из <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> для `IID_IOleUndoManager`. Хранить указатель <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Вызовите `QueryInterface` на `IOleUndoManager` для `IID_IOleCommandTarget`. Хранить указатель <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Ретрансляции вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> вызовы сохраненного `IOleCommandTarget` интерфейса для следующих команд StandardCommandSet97:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Вызовите `QueryInterface` на `IOleUndoManager` для `IID_IVsChangeTrackingUndoManager`. Хранить указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Использование указателя для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> для вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> методы.  
  
5.  Вызовите `QueryInterface` на `IOleUndoManager` для `IID_IVsLinkCapableUndoManager`.  
  
6.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> в документе, который также реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> интерфейса. При закрытии документа вызовите `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  При закрытии документа вызовите `QueryInterface` на ваш диспетчер отмены для `IID_IVsLifetimeControlledObject`.  
  
8.  Вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. При внесении изменений в документ, вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> в диспетчере с `OleUndoUnit` класса. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Метод сохраняет ссылку на объект, обычно его освобождения непосредственно после <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 `OleUndoManager` Класс представляет экземпляр стека одной операции отката. Таким образом имеется один объект диспетчер отмены каждой сущности данных, отслеживаемые для отмены или повтора.  
  
> [!NOTE]
>  Хотя объект диспетчер отмены широко используется текстовый редактор, это общий компонент, не имеет определенного поддержки для текстового редактора. Если требуется для поддержки многоуровневого отмены или повтора, для этого можно использовать этот объект.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Как: очистить стек отмены](../extensibility/how-to-clear-the-undo-stack.md)