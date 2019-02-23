---
title: Контролировать события | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8fbe2f3c3835c55fffefe4692c4e8779b48e9c5e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683393"
---
# <a name="control-events"></a>События элементов управления
Необходимо отправить события во время выполнения управляемой программы. Все события отправляются с помощью [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) интерфейс и атрибутами, которые необходимо реализовать [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) метод.

## <a name="additional-methods"></a>Дополнительные методы
 Некоторые события требуют реализации дополнительных методов следующим образом:

- Отправка [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) интерфейс при инициализации модуля отладки (DE), необходимо реализовать [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) метод.

- Управление выполнением, необходимо реализовать такие события элемента управления, как [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) и[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) интерфейсов. **IDebugBreakEvent2** необходим только для асинхронных разрывов.

- Шаг с заходом в функции, необходимо реализовать [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) интерфейс и его методы.

  События, производное от точки останова требуется реализация [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), и [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) интерфейсы, а также [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) и [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) методы.

  Асинхронное выражение вычисления требуется, как реализовать [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) интерфейса и его [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md) [и GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) методы.

  Синхронных событий требуется реализация [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) метод.

  Модуль записи выходных данных стиль строки, необходимо реализовать [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) метод.

## <a name="see-also"></a>См. также
- [Выполнение управления и состояние оценки](../../extensibility/debugger/execution-control-and-state-evaluation.md)