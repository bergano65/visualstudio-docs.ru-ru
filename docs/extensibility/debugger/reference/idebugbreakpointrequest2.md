---
title: IDebugBreakpointRequest2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f30f9698c9c81322edd6935b40c16cad6f46024c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734915"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Этот интерфейс представляет информацию, необходимую для создания и связывания любого типа точки разрыва.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Менеджер отладки сеанса (SDM) обычно реализует этот интерфейс.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Отладка двигателя (DE) получает этот интерфейс через вызов [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) для того, чтобы создать отложенный пункт разрыва. Звонок в [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) может получить этот интерфейс из DE.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBreakpointRequest2`.

|Метод|Описание|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Получает тип определения местоположения точки разрыва этого запроса точки разрыва.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Получает информацию о запросе точки разрыва, описывающая этот запрос точки разрыва.|

## <a name="remarks"></a>Примечания
 После загрузки отладки программы вызов [bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) связывает отложенную точку разрыва с запрашиваемым местоположением в программе.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
