---
title: Оценка выражения в режиме перерыва (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738724"
---
# <a name="expression-evaluation-in-break-mode"></a>Оценка выражения в режиме перерыва
В следующем разделе описывается процесс, который происходит, когда отладчик находится в режиме перерыва и должен провести оценку выражения.

## <a name="expression-evaluation-process"></a>Процесс оценки экспрессии
 Ниже приведены основные шаги, связанные с оценкой выражения:

1. Менеджер отладки сеанса (SDM) вызывает [IDebugStackFrame2::GetExpressionContext,](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) чтобы получить интерфейс контекста выражения, [IDebugExpressionExpression2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Затем SDM вызывает [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) со строкой для разбора.

3. Если ParseText не возвращается S_OK, причина ошибки возвращается.

     -в противном случае-

     Если ParseText возвращает S_OK, SDM может вызвать либо [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [IDebugExpression2::EvaluateAsync,](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) чтобы получить окончательное значение из разобрана выражения.

    - При `IDebugExpression2::EvaluateSync`использовании интерфейса обратного вызова данный интерфейс передает непрерывный процесс оценки. Окончательное значение возвращается в интерфейсе [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

    - При `IDebugExpression2::EvaluateAsync`использовании интерфейса обратного вызова данный интерфейс передает непрерывный процесс оценки. Как только оценка завершена, EvaluateAsync отправляет интерфейс [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) через обратный вызов. С помощью этого интерфейса события, окончательное значение результатов с [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>См. также
- [События отладки вызова](../../extensibility/debugger/calling-debugger-events.md)
