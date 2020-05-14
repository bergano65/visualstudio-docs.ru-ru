---
title: IEnumDebugПроцессы2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b9fe0e96ade081e8da11b5e1c06c5b45279b10b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715750"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Этот интерфейс перечисляет процессы, работающие на порту отладки.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик пользовательских портов реализует этот интерфейс, чтобы предоставить список процессов, выполняемых в порту.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Visual Studio вызывает [EnumProcesses,](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugProcesses2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Извлекает определенное количество процессов в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Пропускает определенное количество процессов в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Получает количество процессов в регистраторе.|

## <a name="remarks"></a>Примечания
 Visual Studio использует этот интерфейс для заполнения окна **Процессов.**

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
