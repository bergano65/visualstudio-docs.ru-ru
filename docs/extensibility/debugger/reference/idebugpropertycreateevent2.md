---
title: IDebugPropertyCreateEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31764e62f53304d30305f8326c6ab887ffa69e53
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457509"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Этот интерфейс отправляется ядром отладки (DE) диспетчер отладки сеансов (SDM) при создании свойства, связанного с конкретным документом.

## <a name="syntax"></a>Синтаксис

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 DE реализует этот интерфейс, чтобы сообщить, что было создано свойство. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс. Этот интерфейс реализуется в том случае, если DE создал свойство, связанное с скрипт, который был загружен или создан, и если этот скрипт должен отображаться в интегрированной среде разработки.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 DE создает и отправляет этот объект события передавали создано свойство. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны метод `IDebugPropertyCreateEvent2` интерфейс.

|Метод|Описание|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Возвращает новое свойство.|

## <a name="remarks"></a>Примечания
 Если свойство имеет определенному документу или сценарий, связанный с ним, DE отправляют данное событие для обновления SDM **документы скриптов** окно с именем документа. Вызывает SDM [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) с аргументом `guidDocument` извлекаемого `VARIANT` содержащий [IUnknown](/cpp/atl/iunknown) указатель. Вызывает SDM [QueryInterface](/cpp/atl/queryinterface) на этот указатель для получения [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс, который используется для обновления **документы скриптов** окна.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)