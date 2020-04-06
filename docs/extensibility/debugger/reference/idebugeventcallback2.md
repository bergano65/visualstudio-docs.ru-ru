---
title: IDebugEventCallback2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729885"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Этот интерфейс используется движком отладки (DE) для отправки событий отладки менеджеру отладки сеанса (SDM).

## <a name="syntax"></a>Синтаксис

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]реализует этот интерфейс для получения событий из движка отладки.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Отладка двигателя обычно получает этот интерфейс, когда SDM звонки [Прикрепите,](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [Прикрепите](../../../extensibility/debugger/reference/idebugengine2-attach.md), или [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Отладка двигателя отправляет события в SDM, вызывая [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEventCallback2`.

|Метод|Описание|
|------------|-----------------|
|[Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Отправляет уведомления о событиях отладки в SDM.|

## <a name="remarks"></a>Примечания
 Хотя [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) указывают, что они принимают `IDebugEventCallback2` интерфейс, это не так, и указатель интерфейса всегда будет нулевая стоимость. Вместо этого, отладка `IDebugEventCallback2` двигателя должны использовать интерфейс, полученный в вызов [прикрепить,](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [прикрепить](../../../extensibility/debugger/reference/idebugengine2-attach.md), или [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Если пакет реализует [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) в управляемом коде, настоятельно рекомендуется <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> ссылаться на различные интерфейсы, которые передаются в [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
