---
title: IDebugEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729907"
---
# <a name="idebugevent2"></a>IDebugEvent2
Этот интерфейс используется для передачи как критической информации отладки, например остановки в точке разрыва, так и некритической информации, например, сообщения отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) и поставщик пользовательских портов реализуют этот интерфейс на том же объекте, что и все другие интерфейсы событий.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используя аргумент идентификатор интерфейса (IID), приведенный [событию](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) или [событию,](../../../extensibility/debugger/reference/idebugportevents2-event.md)диспетчер `IDebugEvent2` отладки сеанса (SDM) вызывает [queryInterface](/cpp/atl/queryinterface) на интерфейсе для получения соответствующего интерфейса события.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Получает атрибуты для этого события отладки.|

## <a name="remarks"></a>Примечания
 Более конкретные интерфейсы событий, такие как [IDebugBreakpointEvent2,](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)не вытекают из интерфейса IDebugEvent2, `IDebugEvent2`а реализуются как отдельный интерфейс на том же объекте, что и .

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
