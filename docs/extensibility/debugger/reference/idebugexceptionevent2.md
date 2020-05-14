---
title: IDebugExceptionEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbd53d56b21886e972b33c219367edd603cbf0d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729775"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Движок отладки (DE) отправляет этот интерфейс менеджеру отладки сеанса (SDM) при вбрасывании исключения в выполняемую в настоящее время программу.

## <a name="syntax"></a>Синтаксис

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс, чтобы сообщить, что в отладке программы произошло исключение. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. SDM использует [QueryInterface](/cpp/atl/queryinterface) для `IDebugEvent2` доступа к интерфейсу.

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект этого события для сообщения об исключении. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) которая поставляется SDM при подключении к отладке программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugExceptionEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Получает подробную информацию об исключении, которое произвело это событие.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Получает читаемое человеком описание для брошенного исключения, которое произвело это событие.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Определяет, поддерживает ли отладка двигателя (DE) возможность передачи этого исключения в программу, которая отлажется при возобновлении выполнения.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Уточняется, следует ли передавать исключение программе, которая отлажается при возобновлении выполнения, или следует отказаться от этого исключения.|

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Примечания
 Перед отправкой события DE проверяет, было ли это событие исключения назначено первым или вторым исключением по предыдущему вызову [SetException.](../../../extensibility/debugger/reference/idebugengine2-setexception.md) Если исключение было признано исключением первого `IDebugExceptionEvent2` шанса, событие отправляется в SDM. В противном случае DE дает приложению возможность справиться с исключением. Если обработчик исключений не предусмотрен, и если исключение было `IDebugExceptionEvent2` назначено в качестве исключения второго шанса, событие отправляется в SDM. В противном случае DE возобновляет выполнение программы, а операционная система или время выполнения обрабатывает исключение.

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
