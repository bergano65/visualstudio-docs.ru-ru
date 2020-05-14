---
title: IDebugBreakpointBoundEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7943addb4334710da3252a4d822330e45b6e0f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735312"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Этот интерфейс сообщает менеджеру отладки сеанса (SDM), что отложенная точка разрыва была успешно привязана к загруженной программе.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс как часть своей поддержки точек разрыва. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот `IDebugEvent2` интерфейс (SDM использует [queryInterface](/cpp/atl/queryinterface) для доступа к интерфейсу).

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект события, когда отложенная точка разрыва успешно привязана к отладке программы. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) поставляемой SDM при его подключении к отладке программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBreakpointBoundEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Получает отложенную точку разрыва, которая в настоящее время связана.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Создает перечисление моментов, которые были связаны на этом событии.|

## <a name="remarks"></a>Примечания
 Всякий раз, когда точка разрыва связана, событие отправляется в SDM. Если точка разрыва не может быть связана, отправляется [IDebugBreakpointErrorEvent2;](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) в противном случае, отправляется. `IDebugBreakpointBoundEvent2`

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
