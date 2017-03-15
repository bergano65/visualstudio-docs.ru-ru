---
title: "IDebugDocumentTextEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2"
helpviewer_keywords: 
  - "Интерфейс IDebugDocumentTextEvents2"
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс используется для оповещения среды Visual Studio об изменениях к исходному документу, которые предоставляются обработчиком отладки.  
  
## Синтаксис  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, чтобы поддерживать внесения изменений в исходный код.  Этот интерфейс обычно реализуется для одного и того же объекта, реализующего [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс.  
  
## Замечания для вызывающих объектов  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] получает этот интерфейс через вызов  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> метод.  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> интерфейс полученного в результате вызова  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> метод.  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс полученного вызовом метода  [QueryInterface](/visual-cpp/atl/queryinterface) метод  [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugDocumentTextEvents2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Указывает, что весь документ был удален.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Извещает пакет отладки, текст вводило в документ.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Извещает пакет отладки, текст выполненного из документа.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Извещает пакет отладки, текст заменило в документе.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Извещает пакет отладки, которое помещает СМС атрибуты было обновлено в документе.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Уведомляет приемник событий, что атрибуты документа обновляются.|  
  
## Заметки  
 Только отладка обработчики, которые предоставляют свои документы и воспользоваться преимуществами `IDebugDocumentTextEvent2` интерфейс.  Примером этого является обработчик отладки скриптов.  В ходе интерпретации скрипты, новый исходный код можно создавать, отсутствующий в любом файле на диске и известен только к DE.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)