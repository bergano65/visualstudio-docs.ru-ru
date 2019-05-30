---
title: IEnumDebugPorts2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c24edcd5ef47408cd4c11b3d0548ad34516702a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326505"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Этот интерфейс перечисляет порты машинного или порта поставщика.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщика пользовательского порта реализует этот интерфейс для представления список портов, созданные поставщиком. Visual Studio реализует этот интерфейс для поддержки свой собственный поставщик порта.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) для получения этого интерфейса, представляющий список портов, созданные поставщика порта. Вызовите [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) для получения этого интерфейса, представляющий список портов, которые были сохранены на диск.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugPorts2`.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Извлекает указанное число портов в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Пропускает заданное число портов в последовательности перечисления.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Получает количество портов в перечислителе.|

## <a name="remarks"></a>Примечания
 Visual Studio использует этот интерфейс, помогающий заполнить Мой список портов, используемых для присоединения к процессам.

 Обычно модуль отладки не использует этот интерфейс.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)