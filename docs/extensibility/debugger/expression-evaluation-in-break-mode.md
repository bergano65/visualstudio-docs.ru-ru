---
title: Вычисление выражений в режиме приостановки выполнения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 852b4284bbbf59ce8f3964d98f0464e583f1444f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028677"
---
# <a name="expression-evaluation-in-break-mode"></a>Вычисление выражений в режиме приостановки выполнения
Следующий раздел описывает процесс, который возникает, когда отладчик находится в режиме приостановки выполнения и следует проводить вычисления выражения.  
  
## <a name="expression-evaluation-process"></a>Процесс оценки выражения  
 Ниже приведены основные шаги процесса в вычислении выражения.  
  
1.  Диспетчер отладки сеансов (SDM) вызывает [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) Чтобы получить интерфейс контекста выражения, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Затем вызывает SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) со строкой, чтобы выполнить синтаксический анализ.  
  
3.  Если ParseText не возвращает значение S_OK, возвращается причина ошибки.  
  
     -в противном случае —  
  
     Если ParseText возвращает S_OK, SDM может затем вызвать либо метод [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для получения окончательного значения из проанализированное выражение.  
  
    -   При использовании `IDebugExpression2::EvaluateSync`, этот интерфейс заданного обратного вызова сообщает непрерывный процесс оценки. Конечное значение возвращается в [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс.  
  
    -   При использовании `IDebugExpression2::EvaluateAsync`, этот интерфейс заданного обратного вызова сообщает непрерывный процесс оценки. По завершении оценки EvaluateAsync отправляет [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) интерфейса через обратный вызов. С помощью этого интерфейса событий, конечное значение результатов для [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)