---
title: IEnumDebugPortSuppliers2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de0bfc5b387df9b347e4a58d97601a5e1e70f1a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715936"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Этот интерфейс перечисляет поставщиков портов.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Visual Studio реализует этот интерфейс, чтобы представлять список поставщиков портов.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [EnumPortSuppliers,](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) чтобы получить список поставщиков портов.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugPortSuppliers2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Извлекает определенное количество поставщиков портов в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Пропускает определенное число поставщиков портов в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Получает количество поставщиков порта в регистраторе.|

## <a name="remarks"></a>Примечания
 Отладка двигателя, как правило, не нужно, чтобы получить этот интерфейс.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
