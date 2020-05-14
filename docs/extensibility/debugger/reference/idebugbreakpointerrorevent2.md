---
title: IDebugBreakpointErrorEvent2 (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09cb93f0f16420e56104f371d9caab262873390f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735046"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Этот интерфейс сообщает менеджеру отладки сеанса (SDM), что отложенная точка разрыва не может быть привязана к загруженной программе либо из-за предупреждения, либо из-за ошибки.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс как часть своей поддержки точек разрыва. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот `IDebugEvent2` интерфейс (SDM использует [queryInterface](/cpp/atl/queryinterface) для доступа к интерфейсу).

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект события, когда отложенная точка разрыва не может быть привязана к отладке программы. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) поставляемой SDM при его подключении к отладке программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBreakpointErrorEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Получает интерфейс [IDebugErrorBreakpoint2,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) описывающий предупреждение или ошибку.|

## <a name="remarks"></a>Примечания
 Всякий раз, когда точка разрыва связана, событие отправляется в SDM. Если точка разрыва не может `IDebugBreakpointErrorEvent2` быть связана, отправляется отправка; в противном случае отправляется [IDebugBreakpointBoundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)

 Например, когда условие, связанное с ожидающим точкой разрыва, не позволяет разобрать или оценить, отправляется предупреждение о том, что отложенная точка разрыва не может быть связана в данный момент. Это может произойти, если код точки разрыва еще не загружен.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
