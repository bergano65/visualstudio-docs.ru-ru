---
title: "Практическое руководство: реализация управления отмены | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - отменить управления"
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: реализация управления отмены
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Основной интерфейс, используемый для управления отката <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, который реализован средой.  Для поддержки управления отката, реализуйте отдельные единицы отката \(т е <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, который может содержать несколько отдельных шагов.  
  
 Способ реализации элемента управления отката, зависит от того, поддерживает ли данный редактор несколько представлений или нет.  Процедуры для каждой реализации детализированы в следующих разделах.  
  
## Случаи, когда редактор поддерживает одно представление  
 В этом сценарии редактор не поддерживает несколько представлений.  Только один редактора и один документ, и они поддерживают откат.  Используйте следующую процедуру для реализации управление отката.  
  
#### Rollback для поддержки управления редактора единый\-вида  
  
1.  Вызов `QueryInterface` на  `IServiceProvider` интерфейс на границе окна  `IOleUndoManager`из объекта представления документа, чтобы открыть диспетчер отката \(`IID_IOLEUndoManager`\).  
  
2.  Если представление находится в границы окна, оно получает указатель сайта, оно может использовать для вызова `QueryInterface` для  `IServiceProvider`.  
  
## Случаи, когда редактор поддерживает несколько представлений  
 Если существует документ и разделение представления, то обычно один диспетчер отката, связанный с документом.  Все единицы отката размещаются на одном диспетчере отката, связанном с объектом данных документа.  
  
 Вместо представления при запросе диспетчера отката, что по одному для каждого представления вызовы объекта данных документа <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> создать диспетчер отката, указав идентификатор класса CLSID\_OLEUndoManager.  Идентификатор класса определен в файле OCUNDOID.h.  
  
 При использовании <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> чтобы создать собственный экземпляр диспетчера отката, используйте следующую процедуру в обработчик в диспетчер отката среды.  
  
#### Пользовательский диспетчер отката в обработчик среды  
  
1.  Вызов `QueryInterface` в объекте, возвращенном из  <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> для  `IID_IOleUndoManager`.  Сохраните указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Вызов `QueryInterface` на  `IOleUndoManager` для  `IID_IOleCommandTarget`.  Сохраните указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Relay ваше <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> и  `IOleCommandTarget` вызывает, которые хранят  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> интерфейс для следующих команд StandardCommandSet97:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Вызов `QueryInterface` на  `IOleUndoManager` для  `IID_IVsChangeTrackingUndoManager`.  Сохраните указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Используйте указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>вызов  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> "  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>методы.  
  
5.  Вызов `QueryInterface` на  `IOleUndoManager` для  `IID_IVsLinkCapableUndoManager`.  
  
6.  Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> вместе с документом, который также должен реализовать  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> интерфейс.  Если документ закрыт, вызовите `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Если документ закрыт, вызовите `QueryInterface` в диспетчере отката для  `IID_IVsLifetimeControlledObject`.  
  
8.  Вызов метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. При внесении изменений в документе, вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> в диспетчере с  `OleUndoUnit` класс.  <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> метод хранит ссылку на объект, поэтому, как правило, она сразу после выпуска  <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 `OleUndoManager` класс представляет отдельный экземпляр стек отката.  Таким образом, один объект диспетчера отката в сущность данных, отслеживанными для отката или повтора.  
  
> [!NOTE]
>  Пока объект диспетчера отката широко используется текстовым редактором, общий компонент, который не имеет конкретную поддержку текстового редактора.  Если требуется поддерживать многоуровневые отката или повтора, то можно использовать этот объект.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Практическое руководство: Очистка стека отмены](../extensibility/how-to-clear-the-undo-stack.md)