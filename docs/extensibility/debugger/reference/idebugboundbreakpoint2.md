---
title: IDebugBoundBreakpoint2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4d22b10085baefeb3a0286c1b4edcb5876c0dac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735421"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Этот интерфейс представляет собой точку разрыва, которая привязана к местоположению кода.

## <a name="syntax"></a>Синтаксис

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс как часть своей поддержки точек разрыва.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов [в Связывание](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создает этот интерфейс. Звонки в [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) и [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) также могут получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBoundBreakpoint2`.

|Метод|Описание|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Получает отложенную точку разрыва, из которой была создана указанная точка разрыва.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Получает состояние этой связанной точки разрыва.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Получает текущий подсчет хитов для этой связанной точки разрыва.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Получает разрешение точки разрыва, описывающая эту точку разрыва.|
|[Включение](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Позволяет или отсваивает точку разрыва.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Устанавливает количество попадания для этой связанной точки разрыва.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Устанавливает или изменяет условие, связанное с этой точкой разрыва.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Устанавливает или изменяет количество пропусков, связанное с этой связанной точкой разрыва.|
|[Удалить](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет точку останова.|

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Далее](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
