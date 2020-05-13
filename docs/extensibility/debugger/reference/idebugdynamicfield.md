---
title: IDebugDynamicField (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731311"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Этот интерфейс представляет собой тип переменной.

## <a name="syntax"></a>Синтаксис

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован поставщиками символов в качестве базового класса для любого типа, который может быть определен во время выполнения. Это только для управляемого кода.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс представляет собой базовый класс, из которого можно получить более специализированные интерфейсы.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 Этот интерфейс не поставляет никаких методов, `IDebugField`кроме тех, которые унаследованы от .

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
