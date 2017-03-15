---
title: "IDebugLoadCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugLoadCompleteEvent2"
helpviewer_keywords: 
  - "IDebugLoadCompleteEvent2"
ms.assetid: 37eb7360-28e9-4273-862a-4c17f22af690
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugLoadCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс передается с помощью обработчика отладки \(DE\) к сеансу отладки \(SDM\) диспетчер когда программа загрузки, но до любой код выполняется.  
  
## Синтаксис  
  
```  
IDebugLoadCompleteEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, чтобы информировать, что программа была успешно загружена.   IDebugEvent2 интерфейс должен быть реализован в одном объекте, как этот интерфейс.  SDM использует [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс.  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события для оповещения о том, что программа была успешно загружена.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставленные SDM, когда он вложило в отлаживаемом программе.  
  
## Заметки  
 Это событие и остановки событие должно иметь `EVENT_STOPPING` пометить для атрибутов набор событий.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)