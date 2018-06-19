---
title: Вычисление выражений в режиме приостановки выполнения | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66c69d6dc3dbce328e519f6d078e0aa4a5208ca0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100290"
---
# <a name="expression-evaluation-in-break-mode"></a>Вычисление выражений в режиме приостановки выполнения
Далее описывается процесс, который возникает, когда отладчик находится в режиме приостановки выполнения и необходимо проводить вычисления выражения.  
  
## <a name="expression-evaluation-process"></a>Процесс вычисления выражения  
 Существуют следующие основные шаги по оценке выражения:  
  
1.  Диспетчер сеансов отладки (SDM) вызывает [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения интерфейса контекста выражения, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Затем вызывает SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) со строкой для синтаксического анализа.  
  
3.  Если ParseText не возвращает значение S_OK, возвращается причину ошибки.  
  
     -в противном случае —  
  
     Если ParseText возвращает значение S_OK, SDM может затем вызвать [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для получения окончательного значения из проанализированных выражения.  
  
    -   В случае с помощью `IDebugExpression2::EvaluateSync`, данный обратный вызов интерфейса используется для связи непрерывный процесс оценки. Конечное значение возвращается в [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейса.  
  
    -   В случае с помощью `IDebugExpression2::EvaluateAsync`, данный обратный вызов интерфейса используется для связи непрерывный процесс оценки. После завершения вычисления отправляет EvaluateAsync [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) интерфейса через обратный вызов. С помощью этого интерфейса события можно получить окончательное значение [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)