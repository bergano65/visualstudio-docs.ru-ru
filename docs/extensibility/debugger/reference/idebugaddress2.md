---
title: IDebugAddress2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10af641162fe9d254eaa3c0c2f5efbf841dc154e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56677647"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Этот интерфейс обеспечивает доступ к Идентификатору процесса, который является владельцем объекта, адрес которого представлен этим интерфейсом.

## <a name="syntax"></a>Синтаксис

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс. Этот интерфейс обеспечивает доступ к Идентификатору процесса, который является владельцем объекта, который связан с этого адреса.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы vtable
 Помимо методов, наследуемых от [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс, этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Извлекает идентификатор процесса, которому принадлежит объект, представленный этим интерфейсом.|

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)