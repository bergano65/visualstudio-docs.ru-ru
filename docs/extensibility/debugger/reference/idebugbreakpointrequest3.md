---
title: IDebugBreakpointЗапрос3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505b0c0b05fa0f14578d770abec6c43ed6b80b01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734830"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Этот интерфейс представляет информацию, необходимую для создания и связывания любого типа точки разрыва. Это расширение [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Менеджер отладки сеанса (SDM) обычно реализует этот интерфейс.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Отладка двигателя (DE) получает доступ к этому интерфейсу, вызывая [queryInterface](/cpp/atl/queryinterface) на интерфейсе IDebugBreakpointRequest2, полученном в [вызове createPendingBreakpoint.](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованных от [IDebugBreakpointRequest2,](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) `IDebugBreakpointRequest3` интерфейс предоставляет следующий метод.

|Метод|Описание|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Получает информацию о запросе точки разрыва, описывающая этот запрос точки разрыва.|

## <a name="remarks"></a>Примечания
 Этот интерфейс используется для предоставления дополнительной информации DE через [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуру. Эта дополнительная информация включает идентификатор поставщика DE (в виде GUID), имя точки трассировки и имя ограничения точки разрыва.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
