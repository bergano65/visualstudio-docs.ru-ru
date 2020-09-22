---
title: Руководство. Реализация управления отменой | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843220"
---
# <a name="how-to-implement-undo-management"></a>Практическое руководство. Реализация управления отменой
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Основным интерфейсом, используемым для управления отменой <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> , является, который реализуется средой. Для поддержки управления отменой реализуйте отдельные блоки отмены (то есть, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> которые могут содержать несколько отдельных шагов).  
  
 Способ реализации управления отменой зависит от того, поддерживает ли редактор несколько представлений или нет. Процедуры для каждой реализации подробно описаны в следующих разделах.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Случаи, когда редактор поддерживает одно представление  
 В этом сценарии редактор не поддерживает несколько представлений. Существует только один редактор и один документ, и они поддерживают отмену. Используйте следующую процедуру для реализации управления отменой.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Поддержка управления отменой для редактора с одним представлением  
  
1. Вызовите `QueryInterface` `IServiceProvider` интерфейс в рамке окна для `IOleUndoManager` , из объекта представления документа, чтобы получить доступ к диспетчеру отмены ( `IID_IOLEUndoManager` ).  
  
2. Когда представление размещается в рамке окна, оно получает указатель сайта, который можно использовать для вызова метода `QueryInterface` `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Случаи, когда редактор поддерживает несколько представлений  
 Если у вас есть разделение документов и представлений, то обычно существует один диспетчер отмены, связанный с самим документом. Все блоки отмены помещаются в один диспетчер отмены, связанный с объектом данных документа.  
  
 Вместо представления запросов для диспетчера отмены, в котором имеется по одному для каждого представления, объект данных документа вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> для создания диспетчера отмены, указав идентификатор класса CLSID_OLEUndoManager. Идентификатор класса определяется в файле ОКУНДОИД. h.  
  
 При использовании <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> для создания собственного экземпляра диспетчера отмены используйте следующую процедуру, чтобы подключить Диспетчер отмены к среде.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Подключение диспетчера отмены к среде  
  
1. Вызовите для `QueryInterface` объекта, возвращенного из <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> для `IID_IOleUndoManager` . Сохраните указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> .  
  
2. Вызовите `QueryInterface` On `IOleUndoManager` для `IID_IOleCommandTarget` . Сохраните указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
3. Ретрансляция <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> вызов хранимого `IOleCommandTarget` интерфейса для следующих команд StandardCommandSet97:  
  
   - кмдидундо  
  
   - кмдидмултилевелундо  
  
   - кмдидредо  
  
   - кмдидмултилевелредо  
  
   - кмдидмултилевелундолист  
  
   - кмдидмултилевелредолист  
  
4. Вызовите `QueryInterface` On `IOleUndoManager` для `IID_IVsChangeTrackingUndoManager` . Сохраните указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> .  
  
    Используйте указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> , чтобы вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> методы, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5. Вызовите `QueryInterface` On `IOleUndoManager` для `IID_IVsLinkCapableUndoManager` .  
  
6. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> с документом, который также должен реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> интерфейс. Когда документ закрывается, вызовите метод `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` .  
  
7. Когда документ будет закрыт, обратитесь к `QueryInterface` диспетчеру отмены для `IID_IVsLifetimeControlledObject` .  
  
8. Вызовите процедуру <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. При внесении изменений в документ вызывайте <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Диспетчер с помощью `OleUndoUnit` класса. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>Метод сохраняет ссылку на объект, поэтому обычно он освобождается сразу после <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> .  
  
   `OleUndoManager`Класс представляет отдельный экземпляр стека отмены. Таким словами, для каждой сущности данных, отслеживаемой для отмены или повтора, существует один объект диспетчера отменяемых объектов.  
  
> [!NOTE]
> Хотя объект «диспетчер отмены» широко используется текстовым редактором, он является общим компонентом, который не имеет специальной поддержки для текстового редактора. Если вы хотите обеспечить поддержку многоуровневой отмены или повтора, можно использовать этот объект.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Практическое руководство. Очистка стека отмены](../extensibility/how-to-clear-the-undo-stack.md)
