---
title: IEnumDebugBoundBreakpoints2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717439"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Этот интерфейс перечисляет связанные точки разрыва, связанные с ожидающим моментом разрыва или связанным событием.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс как часть своей поддержки точек разрыва. Этот интерфейс должен быть реализован, если точки разрыва поддерживаются.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Визуальные студии звонки:

- [EnumBreakpoints,](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) чтобы получить этот интерфейс, представляющий список всех моментов разрыва, которые были срабатываны.

- [EnumBoundBreakpoints,](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) чтобы получить этот интерфейс, представляющий список всех связанных моментов.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) для получения этого интерфейса, представляющего список всех точек разрыва, связанных с этой ожидающей точкой разрыва.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugBoundBreakpoints2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Извлекает определенное количество связанных точек разрыва в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Пропускает определенное количество связанных точек разрыва в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Получает количество связанных моментов в регистраторе.|

## <a name="remarks"></a>Примечания
 Visual Studio использует связанные точки разрыва, представленные этим интерфейсом, для обновления отображения точек разрыва в IDE.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
