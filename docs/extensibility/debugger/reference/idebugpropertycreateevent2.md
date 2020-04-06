---
title: IDebugPropertyСозданиеСобытие2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720928"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Этот интерфейс отправляется движком отладки (DE) менеджеру отладки сеанса (SDM), когда он создает свойство, связанное с конкретным документом.

## <a name="syntax"></a>Синтаксис

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс, чтобы сообщить о создании свойства. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. SDM использует [QueryInterface](/cpp/atl/queryinterface) для `IDebugEvent2` доступа к интерфейсу. Этот интерфейс реализован, если DE создал свойство, связанное с загруженным или созданным скриптом, и если этот скрипт должен появиться в IDE.

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект события для сообщения о создании объекта. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) поставляемой SDM при подключении к отладочной программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показан `IDebugPropertyCreateEvent2` метод интерфейса.

|Метод|Описание|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Получает новое свойство.|

## <a name="remarks"></a>Примечания
 Если с ним связан определенный документ или скрипт, DE может отправить это событие в SDM для обновления окна **документов с** указанием имени документа. SDM вызовет [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) с `guidDocument` аргументом, `VARIANT` чтобы получить содержащий [указатель IUnknown.](/cpp/atl/iunknown) SDM вызовет [queryInterface](/cpp/atl/queryinterface) на этом указателе для получения интерфейса [IDebugDocument2,](../../../extensibility/debugger/reference/idebugdocument2.md) который используется для обновления окна **документов скрипта.**

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
