---
title: IEnumDebugBoundBreakpoints2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40097fab8a45a08ce11c9f58fa22f4464174ef32
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680208"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Этот интерфейс перечисляет связанных точек останова, связанные с ожидающая точка останова или точка останова привязки событий.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс как часть поддержки точек останова. Этот интерфейс должен быть реализован, если поддерживаются точки останова.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Visual Studio вызывает:

-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) для получения этого интерфейса, представляющий список всех точек останова, которые были активированы.

-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) для получения этого интерфейса, представляющий список всех точек останова, которые были привязаны.

-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) для получения этого интерфейса, представляющий список всех точек останова, привязанного к этой ожидающая точка останова.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugBoundBreakpoints2`.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Извлекает указанное число связанных точек останова в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Пропускает заданное число связанных точек останова в последовательности перечисления.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Возвращает количество связанных точек останова в перечислителе.|

## <a name="remarks"></a>Примечания
 Visual Studio использует связанных точек останова, представленного этим интерфейсом, чтобы обновить список точек останова в интегрированной среде разработки.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)