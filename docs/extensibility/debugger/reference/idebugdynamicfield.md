---
title: IDebugDynamicField | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58a4838afc0d52ab60ae0a11de419393d68dfc06
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351334"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Этот интерфейс представляет тип переменной.

## <a name="syntax"></a>Синтаксис

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиками символ как базовый класс для любого типа, которое можно определить во время выполнения. Это только для управляемого кода.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс представляет базовый класс, от которого можно наследовать более специализированных интерфейсов.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Этот интерфейс не предоставляет никаких методов, кроме тех, унаследованные от `IDebugField`.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)