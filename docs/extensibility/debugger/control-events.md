---
title: "События элементов управления | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка событий [отладка SDK]"
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# События элементов управления
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Для отправки событий, отслеживаемого во время выполнения программы.  Все события передаются с помощью [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) интерфейс и имеет атрибуты, которые требуют реализации  [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) метод.  
  
## Дополнительные методы  
 Некоторые события требуют реализацию дополнительных методов следующим образом:  
  
-   Отправить [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) интерфейс когда обработчик отладки \(DE\) инициализирован требует реализации  [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) метод.  
  
-   Управление выполнения требует реализации таких событий элемента управления как [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) и[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) интерфейсы.   IDebugBreakEvent2 требуется только для асинхронных операций.  
  
-   Пошаговое выполнение функций требует реализации IDebugStepCompleteEvent2 интерфейс и его методы.  
  
 События, наследуемого от точки останова требует реализации [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)"  [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)и  [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) интерфейсы, а также  [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) и  [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) методы.  
  
 Асинхронное вычисление выражений требует реализации [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) интерфейс и сво  [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[и GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) методы.  
  
 Синхронные события требуется реализация [IDebugEngine2:: ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) метод.  
  
 Для обработчика для записи выходных данных строка\-стиля, необходимо реализовать [IDebugOutputStringEvent2:: GetString](../Topic/IDebugOutputStringEvent2::GetString.md) метод.  
  
## См. также  
 [Управление выполнением и оценки состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)