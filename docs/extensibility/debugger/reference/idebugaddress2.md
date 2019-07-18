---
title: IDebugAddress2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66fd149bc3eed7633586c156f6493c8febcbeaac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330352"
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