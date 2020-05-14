---
title: IEnumDebugPorts2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3cc46ef8abb6ef1fbb8f072d97b0fc4a537af1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716103"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Этот интерфейс перечисляет порты поставщика машины или порта.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик пользовательских портов реализует этот интерфейс, чтобы представить список портов, созданных поставщиком. Visual Studio реализует этот интерфейс в поддержку собственного портового поставщика.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [в EnumPorts,](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) чтобы получить этот интерфейс, представляющий список портов, созданных поставщиком порта. Позвоните [В EnumPersistedPorts,](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) чтобы получить этот интерфейс, представляющий список портов, которые были сохранены на диске.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugPorts2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Извлекает определенное количество портов в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Пропускает определенное количество портов в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Получает количество портов в регистраторе.|

## <a name="remarks"></a>Примечания
 Visual Studio использует этот интерфейс, чтобы помочь заполнить список портов, используемых для присоединения к процессам.

 Движок отладки обычно не использует этот интерфейс.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
