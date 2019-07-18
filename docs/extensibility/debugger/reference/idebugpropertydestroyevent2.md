---
title: IDebugPropertyDestroyEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a52e9a1a3723566dd7a2dbdfc3cfe1a4d41261ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322746"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Этот интерфейс отправляется ядром отладки (DE) диспетчер отладки сеансов (SDM) Если свойство, связанный с конкретным документом является уничтожить.

## <a name="syntax"></a>Синтаксис

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 DE реализует этот интерфейс, чтобы сообщить, что свойство было уничтожено. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс. Этот интерфейс реализуется в том случае, если DE ранее уже создано свойство, связанное с помощью сценария; уничтожение свойство удаляет связанный скрипт в интегрированной среде разработки.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 DE создает и отправляет этот объект события передавали свойство было уничтожено. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны метод `IDebugPropertyDestroyEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Возвращает свойство будут уничтожены.|

## <a name="remarks"></a>Примечания
 См. в разделе "Примечания" для [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) Дополнительные сведения о том, почему эти события используются.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)