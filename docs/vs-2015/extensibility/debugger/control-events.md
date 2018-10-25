---
title: Контролировать события | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb3332ead5928be9127d64c3870b3212cd6754fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837910"
---
# <a name="control-events"></a>События элементов управления
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)

