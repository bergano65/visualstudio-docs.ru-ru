---
title: "IDebugDocument2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2"
helpviewer_keywords: 
  - "Интерфейс IDebugDocument2"
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocument2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет исходный документ.  
  
## Синтаксис  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## Примечания по реализации  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] обычно реализует этот интерфейс.  Отладчик \(DE\) также может реализовать этот интерфейс, когда необходимо указать исходный код и источник не существует на диске.  В таких случаях DE также реализации бы [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) и  [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) интерфейсы, а также некоторые дополнительные методы  [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) и  [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) интерфейсы.  
  
## Замечания для вызывающих объектов  
 Методы `IDebugDocumentContext2`"  `IDebugDisassemblyStream2`"  `IDebugDocumentPosition2`и  `IDebugActivateDocumentEvent2` интерфейсы возвращают этот интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugDocument2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Возвращает имя документа в одной из следующих форм.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Получает идентификатор класса документа.|  
  
## Заметки  
 Этот интерфейс реализуется только если DE почту исходный код.  Например, при отладке скрипт на странице HTML, DE почту исходный код, поскольку источник будет загружен или создаваемый динамически и не существует в виде файла на диске.  Отладку традиционных языков, как C\+\+, этот интерфейс не требуется реализовывать.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)   
 [GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)