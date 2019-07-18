---
title: IDebugBreakpointErrorEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bae4a63ef03ca3b8d3fa642f7333ff2357084b47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352937"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Этот интерфейс указывает диспетчер отладки сеансов (SDM), ожидающая точка останова не были привязаны в загрузить программу, из-за предупреждение или ошибку.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 DE реализует этот интерфейс как часть поддержки точек останова. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс).

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 DE создает и отправляет этот объект события в том случае, если ожидающая точка останова не может быть привязано к отлаживаемой программы. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, если он присоединен к отлаживаемой программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBreakpointErrorEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Получает [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) интерфейс, который описывает предупреждения или ошибки.|

## <a name="remarks"></a>Примечания
 Каждый раз, когда привязана точка останова, событие передается SDM. Если точка останова не может быть привязана, `IDebugBreakpointErrorEvent2` передаются; в противном случае — значение [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) отправляется.

 К примеру Если условие, связанное с ожидающая точка останова не удается проанализировать или оценить, предупреждение отправляется, что ожидающая точка останова не удается найти метод в настоящее время. Это может произойти, если код для точки останова еще не загружен.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)