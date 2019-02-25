---
title: IDebugThreadDestroyEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2
helpviewer_keywords:
- IDebugThreadDestroyEvent2
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7fc94a1289f8b65798f5ad0dab1b4e82bf76b533
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700228"
---
# <a name="idebugthreaddestroyevent2"></a>IDebugThreadDestroyEvent2
Этот интерфейс отправляется ядром отладки (DE) диспетчер отладки сеансов (SDM) при запуске потока для завершения.

## <a name="syntax"></a>Синтаксис

```
IDebugThreadDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 DE реализует этот интерфейс для отчетов, что поток завершен. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 DE создает и отправляет этот объект события отчетов, что поток завершен. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugThreadDestroyEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|Возвращает код выхода потока.|

## <a name="remarks"></a>Примечания
 Visual Studio использует это событие для обновления **потоков** окна.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)