---
title: Вычисление выражений в режиме приостановки выполнения | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738724"
---
# <a name="expression-evaluation-in-break-mode"></a>Вычисление выражений в режиме приостановки выполнения
В следующем разделе описывается процесс, выполняемый, когда отладчик находится в режиме приостановки выполнения и должен выполняться вычисление выражения.

## <a name="expression-evaluation-process"></a>Процесс оценки выражений
 Ниже приведены основные шаги, используемые при вычислении выражения.

1. Диспетчер отладки сеансов (SDM) вызывает [IDebugStackFrame2:: жетекспрессионконтекст](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения интерфейса контекста выражения [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Затем SDM вызывает [IDebugExpressionContext2::P арсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) со строкой, которую необходимо проанализировать.

3. Если Парсетекст не возвращает S_OK, то возвращается причина ошибки.

     ином

     Если Парсетекст возвращает S_OK, то модель SDM может затем вызвать либо [IDebugExpression2:: евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , либо [IDebugExpression2:: евалуатеасинк](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , чтобы получить конечное значение из проанализированного выражения.

    - При использовании `IDebugExpression2::EvaluateSync` данный интерфейс обратного вызова сообщает о текущем процессе вычисления. Окончательное значение возвращается в интерфейсе [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

    - При использовании `IDebugExpression2::EvaluateAsync` данный интерфейс обратного вызова сообщает о текущем процессе вычисления. После завершения оценки Евалуатеасинк отправляет интерфейс [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) через обратный вызов. При использовании этого интерфейса событий итоговое значение выдается с помощью параметра [result](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>См. также раздел
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
