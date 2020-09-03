---
title: IDebugBreakpointResolution2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb5e4f9e32017cfb493aae00a24f9f8184605d1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734748"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Этот интерфейс представляет сведения, описывающие связанную точку останова.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки точек останова. Этот интерфейс предоставляет описание привязанной точки останова, которую диспетчер отладки сеанса использует, когда пользователь просматривает свойства точки останова.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [жетбреакпоинтресолутион](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBreakpointResolution2` .

|Метод|Описание|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Возвращает тип точки останова, представленной этим разрешением.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешении точки останова, описывающие эту точку останова.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
