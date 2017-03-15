---
title: "IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2"
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс передается с помощью обработчика отладки \(DE\) к сеансу отладки \(SDM\) диспетчер когда асинхронная вычисление выражений завершена.  
  
## Синтаксис  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, чтобы информировать завершения оценки выражений запущенной вызовом [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).   IDebugEvent2 интерфейс должен быть реализован в одном объекте, как этот интерфейс.  SDM использует [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс.  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события для оповещения завершения оценки выражений.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставленные SDM, когда он вложило в отлаживаемом программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugExpressionEvaluationCompleteEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Возвращает исходное выражение.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Возвращает результат оценки выражений.|  
  
## Заметки  
 DE должен отправлять данное событие, была ли оценка успешно или нет.  
  
 Если не завершилась успешно, то оценка `DEBUG_PROPINFO_VALUE` и  `DEBUG_PROPINFO_ATTRIB` флаги не будут установлены в  [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структура, которая возвращается оператором  [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) \(  [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект создан и возвращен в DE  `IDebugExpressionEvaluationCompleteEvent2` событие, если оценка завершилась ошибкой\).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)