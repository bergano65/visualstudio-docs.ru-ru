---
title: "IDebugExpression2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2"
helpviewer_keywords: 
  - "Интерфейс IDebugExpression2"
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugExpression2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет проанализированное выражение готово для привязки и оценки.  
  
## Синтаксис  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, представляющий проанализированное выражение готовности быть вычисляемым.  
  
## Замечания для вызывающих объектов  
 Вызов [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) возвращает данный интерфейс.  [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает IDebugExpressionContext2 интерфейс.  Эти интерфейсы доступны, только если была приостановлена отлаживаемой программы и кадр стека доступен.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugExpression2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Вычисляет это выражение в асинхронном режиме.|  
|[Прервать](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает асинхронное вычисление выражений.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Вычисляет это выражение.|  
  
## Заметки  
 Когда программа останавливала сеанс отладки \(SDM\) получает диспетчер кадр стека, вызвав из DE [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  SDM затем вызывает метод [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) доступ  [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс.  Это за вызовом [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) создание  `IDebugExpression2` интерфейс, представляющий проанализированное выражение готовности быть вычисляемым.  
  
 SDM вызывает то [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) OR  [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) фактически вычислить выражение и сгенерировать значение.  
  
 в реализации  `IDebugExpressionContext2::ParseText`использование модели COM, DE  `CoCreateInstance` функция для создания экземпляра средства оценки выражений и возвращает  [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) интерфейс \(см. пример в  `IDebugExpressionEvaluator` интерфейс\).  Затем вызовы DE [Анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) доступ  [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) интерфейс.  Этот интерфейс используется в реализации `IDebugExpression2::EvaluateSync` и  `IDebugExpression2::EvaluateAsync` выполнить вычисление.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)