---
title: IEnumDebugPortSuppliers2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9200c5366fb428371b633cfb0b97f72d8da8b566
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693224"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Этот интерфейс перечисляет поставщики портов.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio реализует этот интерфейс для представления списка поставщиков порт.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) для получения списка поставщиков порт.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugPortSuppliers2`.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Извлекает указанное число поставщикам портов в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Пропускает заданное число поставщиков портов в последовательности перечисления.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Получает номер порта поставщиков в перечислителе.|

## <a name="remarks"></a>Примечания
 Модуль отладки, как правило, необязательно для получения этого интерфейса.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)