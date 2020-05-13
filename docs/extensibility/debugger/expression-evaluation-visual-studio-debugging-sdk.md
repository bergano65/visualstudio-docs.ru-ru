---
title: Оценка экспрессии (Visual Studio Debugging SDK) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738710"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Оценка экспрессии (Visual Studio Debugging SDK)
В режиме перерыва IDE должен оценивать простые выражения, включающие несколько переменных программы. Для выполнения своей оценки движок отладки (DE) должен разобрать и оценить выражение, внесенное в одно из окон IDE.

 Выражения создаются методом [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и представлены полученным интерфейсом [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

 Интерфейс **IDebugExpression2** реализован DE и называет свой метод **EvalAsync** для возврата интерфейса [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) в IDE, чтобы отобразить результаты оценки выражения в IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) возвращает структуру, которая используется для посыл стоимости выражения в окне **смотреть** или в окно **Locals.**

 Отлажательный пакет или диспетчер сеанса (SDM) вызывает [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) или [EvaluateSync,](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) чтобы получить интерфейс [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) представляющий результат оценки. `IDebugProperty2`имеет методы, возвращающие имя, тип и значение выражения. Эта информация появляется в различных окнах отладчиков.

## <a name="using-expression-evaluation"></a>Использование оценки экспрессии
 Чтобы использовать оценку выражения, необходимо реализовать метод [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и все методы интерфейса [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) как показано в следующей таблице.

|Метод|Описание|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Оценивает выражение асинхронно.|
|[Прервать](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Окончание асинхронной оценки выражения.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Оценивает выражение синхронно.|

 Синхронная и асинхронная оценка требует реализации метода [IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Асинхронная оценка экспрессии требует реализации [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>См. также
- [Контроль исполнения и государственная оценка](../../extensibility/debugger/execution-control-and-state-evaluation.md)
