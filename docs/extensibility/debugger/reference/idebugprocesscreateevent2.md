---
title: IDebugProcessCreateEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessCreateEvent2
helpviewer_keywords:
- IDebugProcessCreateEvent2
ms.assetid: c660439d-8b23-4dbb-923e-ebb5e1d7edf5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bf1f6b66ac5f2c7c7164d8cd82096ee1af8cacf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325314"
---
# <a name="idebugprocesscreateevent2"></a>IDebugProcessCreateEvent2
Этот интерфейс отправляется при запуске процесса.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) или поставщика пользовательского порта реализует этот интерфейс, чтобы сообщить, что процесс был создан. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 DE или поставщика пользовательского порта создает и отправляет этот объект события для создания отчета создание процесса. DE отправляет данное событие с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы. Поставщик настраиваемого порта отправляет это событие с помощью [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) интерфейс.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)