---
title: IDebugАдрес2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 402d8c8bcb50c570ff680b8fe1cf8d26f037ba17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736568"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Этот интерфейс обеспечивает доступ к идентификатору процесса, которому принадлежит объект, адрес которого представлен этим интерфейсом.

## <a name="syntax"></a>Синтаксис

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс на том же объекте, который реализует интерфейс [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md) Этот интерфейс обеспечивает доступ к идентификатору процесса, которому принадлежит объект, связанный с этим адресом.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используйте [queryInterface,](/cpp/atl/queryinterface) чтобы получить этот интерфейс из интерфейса [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

## <a name="methods-in-vtable-order"></a>Методы в vtable заказе
 В дополнение к методам, унаследованных от интерфейса [IDebugAddress,](../../../extensibility/debugger/reference/idebugaddress.md) этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Извлекает идентификатор процесса, который владеет объектом, представленным этим интерфейсом.|

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
