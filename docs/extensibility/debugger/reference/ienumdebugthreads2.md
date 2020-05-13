---
title: IEnumDebugThreads2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbe047c08f8e91264163d028c1b40d94cde97fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715091"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Этот интерфейс перечисляет потоки, работающие в текущей сессии отладки.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы представить список потоков в программе.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [EnumThreads,](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) чтобы получить этот интерфейс, представляющий список всех потоков во всех программах, работающих в процессе. Позвоните [EnumThreads,](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) чтобы получить этот интерфейс, представляющий список потоков, работающих в программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugThreads2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Извлекает определенное количество потоков в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Пропускает определенное количество потоков в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущее.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Получает количество потоков в регистраторе.|

## <a name="remarks"></a>Примечания
 Visual Studio обычно получает этот интерфейс для обновления окна **потоков,** а также для получения первого потока списка, для того, чтобы вызвать [Execute,](../../../extensibility/debugger/reference/idebugprocess3-execute.md) [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md), и [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Выполнить](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
