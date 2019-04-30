---
title: IDebugBreakpointRequest2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a984634dbba0fc1d732fe98214a07d8d6c339d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923388"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Этот интерфейс представляет сведения, необходимые для создания и привязки любого типа точки останова.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Диспетчер отладки сеансов (SDM) обычно реализует этот интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Модуль отладки (DE) получает этот интерфейс, посредством вызова [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) для создания ожидающая точка останова. Вызов [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) из DE можно получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBreakpointRequest2`.

|Метод|Описание|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Возвращает тип местоположения точки останова этого запроса точки останова.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Получает сведения о запросе точки останова, описывающее этот запрос точки останова.|

## <a name="remarks"></a>Примечания
 После программа отлаживаемой загрузки, вызов [привязать](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) привязывает ожидающая точка останова в указанное место в программе.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)