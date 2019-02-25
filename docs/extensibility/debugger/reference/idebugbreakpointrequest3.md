---
title: IDebugBreakpointRequest3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c45b1bae11710063d089aeca61a9d20fb6e907a4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691102"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Этот интерфейс представляет сведения, необходимые для создания и привязки любого типа точки останова. Он является расширением [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Диспетчер отладки сеансов (SDM) обычно реализует этот интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Модуль отладки (DE) обращается к этот интерфейс путем вызова [QueryInterface](/cpp/atl/queryinterface) об интерфейсе IDebugBreakpointRequest2, полученных при вызове [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов, наследуемых от [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), `IDebugBreakpointRequest3` интерфейс предоставляет следующий метод.

|Метод|Описание|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Получает сведения о запросе точки останова, описывающее этот запрос точки останова.|

## <a name="remarks"></a>Примечания
 Этот интерфейс используется для предоставления дополнительных сведений для DE через [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры. Эта дополнительная информация включает в себя идентификатор поставщика DE (в виде идентификатора GUID), имя точки трассировки и имя ограничения точки останова.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)