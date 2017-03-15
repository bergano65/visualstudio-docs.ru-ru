---
title: "IDebugFunctionPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionPosition2"
helpviewer_keywords: 
  - "Интерфейс IDebugFunctionPosition2"
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет абстрактную положение функции в исходном документе.  
  
## Синтаксис  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс для представления положения функции в исходный документ.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс предоставляется как часть a [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union \(в частности, a  [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) структура\), которая, в свою очередь, часть  [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) структура, используемая при создании ожидается точка останова.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugFunctionPosition2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Возвращает имя функции, что эта позиция относительно.|  
|[GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)|Получает смещение в байтах от начала функции.|  
  
## Заметки  
 Позиция, представляемое этим интерфейсом на основе текста в частности, a [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) структура.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)