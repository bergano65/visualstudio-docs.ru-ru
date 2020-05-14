---
title: События управления Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739088"
---
# <a name="control-events"></a>Управление событиями
Вы должны отправлять события во время контролируемого выполнения вашей программы. Все события отправляются с помощью интерфейса [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) и имеют атрибуты, требующие реализации метода [IDebugEvent2::GetAttributes.](../../extensibility/debugger/reference/idebugevent2-getattributes.md)

## <a name="additional-methods"></a>Дополнительные методы
 Некоторые события требуют внедрения дополнительных методов:

- Отправка интерфейса [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) при инициализации отладочную движка (DE) требует реализации метода [IDebugEngineCreateEvent2::GetEngine.](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)

- Управление выполнением требует реализации таких событий управления, как интерфейсы [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) и[IDebugStepCompleteEvent2.](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) **IDebugBreakEvent2** требуется только для асинхронных перерывов.

- Переход на функции требует реализации интерфейса [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) и его методов.

  События, происходящие из точек разрыва, требуют реализации интерфейсов [IDebugBreakpointErrorEvent2,](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)и [IDebugBreakpointBoundEvent2,](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) а также [iDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) и [EnumBoundBreakpoints.](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)

  Асинхронная оценка экспрессии требует реализации интерфейса [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) и его методов [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[и GetResult.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

  Синхронные события требуют реализации метода [IDebugEngine2::ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

  Для записи вывода в стиле строки необходимо реализовать метод [IDebugOutputStringEvent2::GetString.](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)

## <a name="see-also"></a>См. также
- [Контроль исполнения и государственная оценка](../../extensibility/debugger/execution-control-and-state-evaluation.md)
