---
title: "Вычисление выражений в режиме приостановки выполнения | Microsoft Docs"
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
  - "режим приостановки выполнения, вычисление выражений"
  - "отладка [отладка SDK], вычисление выражений"
  - "вычисление выражений, в режиме приостановки выполнения"
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Вычисление выражений в режиме приостановки выполнения
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Далее описывается процесс, который происходит, когда отладчик в режиме приостановки выполнения и проведения оценки выражений.  
  
## Процесс оценки выражений  
 Эти основные шаги, необходимые для оценки выражения:  
  
1.  Сеанс отладки вызовы диспетчера \(SDM\) [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) получить интерфейс контекста выражения  [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  SDM затем вызывает метод [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) при строка, которую необходимо проанализировать.  
  
3.  Если ParseText не возвращает значение S\_OK, то причина ошибки возвращается.  
  
     в противном случае \-  
  
     Если ParseText возвращает значение S\_OK, затем может вызвать то SDM [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) OR  [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для получения конечного значения из проанализированного выражения.  
  
    -   в случае использования `IDebugExpression2::EvaluateSync`заданный интерфейс обратного вызова используется для связи текущих процесс оценки.  Конечное значение возвращается в IDebugProperty2 интерфейс.  
  
    -   в случае использования `IDebugExpression2::EvaluateAsync`заданный интерфейс обратного вызова используется для связи текущих процесс оценки.  После завершения EvaluateAsync отправляет вычисление IDebugExpressionEvaluationCompleteEvent2 интерфейс посредством обратного вызова.  С этим интерфейсом события, окончательного значения можно получить с [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)