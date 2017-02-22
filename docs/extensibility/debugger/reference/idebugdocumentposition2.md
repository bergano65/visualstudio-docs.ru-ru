---
title: "IDebugDocumentPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2"
helpviewer_keywords: 
  - "Интерфейс IDebugDocumentPosition2"
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет абстрактную позицию в файле источника.  
  
## Синтаксис  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## Примечания по реализации  
 Visual Studio обычно реализует этот интерфейс.  Отладчик \(DE\) также реализации бы этот интерфейс, если он должен предоставить свой исходный код \(например, если реализуемый DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс\).  
  
## Замечания для вызывающих объектов  
 Этот интерфейс передается в качестве аргумента [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md).  Также предоставляется как часть a [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union \(в частности, a  [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) структура\), которая, в свою очередь, часть  [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) структура, используемая при создании ожидается точка останова.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugDocumentPosition2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Получает имя файла исходного файла, содержащего данную позицию документа.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Возвращает содержащий документ.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Определяет, если данная позиция содержится в заданном документе.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Получает диапазон для этой части документа.|  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)