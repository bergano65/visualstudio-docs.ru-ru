---
title: Оценка выражений Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738828"
---
# <a name="evaluate-expressions"></a>Оценка выражений
Выражения создаются из строк, передаваемых из **Autos,** **Watch,** **quickWatch**или **Immediate** windows. При оценке выражения создается строка, содержащая имя и тип переменной или аргумента и ее значение. Эта строка отображается в соответствующем окне IDE.

## <a name="implementation"></a>Реализация
 Выражения оцениваются, когда программа остановилась в точке разрыва. Само выражение представлено интерфейсом [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) который представляет собой разогнанные выражения, готовые к связыванию и оценке в контексте данной оценки выражения. Кадр стека определяет контекст оценки выражения, который поставляют движок отладки (DE) путем реализации интерфейса [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

 Учитывая пользовательскую строку и интерфейс [IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) отладка (DE) может получить интерфейс [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) передавая строку пользователя методу [IDebugExpressionExpression2::ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Возвращается интерфейс IDebugExpression2, содержащий разображенные выражения, готовые к оценке.

 С `IDebugExpression2` помощью интерфейса DE может получить значение выражения с помощью синхронной или асинхронной оценки выражения, используя [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Это значение, наряду с именем и типом переменной или аргументом, отправляется в IDE для отображения. Значение, имя и тип представлены интерфейсом [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

 Для обеспечения оценки экспрессии DE должен реализовать интерфейсы [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) и [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Как синхронная, так и асинхронная оценка требуют реализации метода [IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

## <a name="see-also"></a>См. также
- [Стек кадры](../../extensibility/debugger/stack-frames.md)
- [Контекст оценки выражения](../../extensibility/debugger/expression-evaluation-context.md)
- [Задачи дебуза](../../extensibility/debugger/debugging-tasks.md)
