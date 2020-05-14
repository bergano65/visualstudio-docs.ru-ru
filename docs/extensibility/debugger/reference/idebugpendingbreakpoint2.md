---
title: IDebugPendingBreakpoint2 (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725650"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Этот интерфейс представляет собой точку разрыва, которая готова привязаться к местоположению кода.

## <a name="syntax"></a>Синтаксис

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс как часть своей поддержки точек разрыва.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов [к CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) создает отложенную точку разрыва из интерфейса [IDebugBreakpointRequest2.](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Вызов [в Связующее положение](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создает `IDebugBreakpoint2` интерфейс, представляющий собой точку разрыва в программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPendingBreakpoint2`.

|Метод|Описание|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет, может ли эта незавершенная точка разрыва связываться с местоположением кода.|
|[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Связывает эту точку разрыва ожидания с одним или несколько местами кода.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Получает состояние этой ожидавной точки разрыва.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Получает запрос точки разрыва, который был использован для создания этой ожидачего точки разрыва.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Переключает виртуализированное состояние этой ожидающего разрыва.|
|[Включение](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает включенное состояние этой ожидающего разрыва.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Устанавливает или изменяет условие, связанное с этой ожидавной точкой разрыва.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Устанавливает или изменяет количество пропусков, связанное с этой ожидавной точкой разрыва.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки разрыва, связанные с этой ожидавшей разрыва.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Перечисляет все точки ошибки, которые были получены в результате этого ожидающего разрыва.|
|[Удалить](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Удаляет эту ожидавную точку разрыва и все точки разрыва, связанные с ней.|

## <a name="remarks"></a>Примечания
 `IDebugPendingBreakpoint2`может рассматриваться как поставщик всей необходимой информации, необходимой для привязки точки разрыва к коду, который может быть применен к одной или многим программам.

 Ожидаемая точка разрыва потенциально может привести к более чем одной точке разрыва. Например, точка разрыва в шаблоне в стиле Сз может создать точку разрыва для каждого уникального экземпляра этого шаблона.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
