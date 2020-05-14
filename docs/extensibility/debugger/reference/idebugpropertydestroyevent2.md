---
title: IDebugPropertyDestroyEvent2 (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce15f389f22513e08b06c0d097cdac4aec3c35bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720903"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Этот интерфейс отправляется движком отладки (DE) диспетчеру отладки сеанса (SDM), когда свойство, связанное с конкретным документом, вот-вот будет уничтожено.

## <a name="syntax"></a>Синтаксис

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс, чтобы сообщить, что свойство было уничтожено. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. SDM использует [QueryInterface](/cpp/atl/queryinterface) для `IDebugEvent2` доступа к интерфейсу. Этот интерфейс реализован, если DE ранее создал свойство, связанное с скриптом; уничтожение свойства удаляет связанный с ней скрипт из IDE.

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект этого события, чтобы сообщить об уничтожении имущества. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) поставляемой SDM при подключении к отладочной программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице `IDebugPropertyDestroyEvent2`показан метод .

|Метод|Описание|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Получает имущество, чтобы быть уничтожены.|

## <a name="remarks"></a>Примечания
 Подробнее о том, почему используются эти события, можно узнать о причинах использования [IDebugPropertyCreateEvent2.](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
