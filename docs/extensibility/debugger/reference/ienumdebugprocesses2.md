---
title: IEnumDebugProcesses2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f59cdc9a257f853f70afe2566d7b06e39f8edc02
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846664"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Этот интерфейс перечисляет процессы, запущенные в порте отладки.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский поставщик портов реализует этот интерфейс для предоставления списка процессов, запущенных в порте.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Visual Studio вызывает [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugProcesses2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Извлекает указанное количество процессов в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Пропускает указанное число процессов в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Возвращает количество процессов в перечислителе.|

## <a name="remarks"></a>Remarks
 Visual Studio использует этот интерфейс для заполнения окна **процессов** .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
