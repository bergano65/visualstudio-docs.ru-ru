title: IDebugMemoryBytes2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56cb234e2295c5c9c08c2a2e9271e1c173524875
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727501"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Этот интерфейс представляет байты памяти.

## <a name="syntax"></a>Синтаксис

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс для представления байтов в памяти.

## <a name="notes-for-callers"></a>Заметки для абонентов
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) возвращает этот интерфейс, чтобы обеспечить доступ к системной памяти. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) и [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) возвращают этот интерфейс, чтобы обеспечить доступ к байтам объекта.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugMemoryBytes2`.

|Метод|Описание|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Читает последовательность байтов, начиная с заданного места.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Пишет `dwCount` байты, `pStartContext`начиная с .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Получает размер, в байтах, памяти, представленной этим интерфейсом.|

## <a name="remarks"></a>Примечания
 Для свойств интерфейс [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) представляющий `IDebugMemoryBytes2` массив, предоставляет интерфейс для доступа к значениям в этом массиве.

 **Представление памяти** Visual Studio вызывает [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) для получения интерфейса `IDebugMemoryBytes2` для доступа к памяти системы. Адрес, к который будет получен, получен путем разбора выражения, введенного в виде адреса в Представление памяти, а затем оценки разобрана выражения с помощью [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для получения интерфейса. `IDebugProperty2` Звонок [в GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) возвращает [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) описывающий адрес памяти. Этот контекст памяти затем передается [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) и [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
