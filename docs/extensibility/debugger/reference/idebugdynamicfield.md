---
title: Идебугдинамикфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6cd81f393b81adb37059106e2d56fd4a3bf2c461
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921161"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Этот интерфейс представляет тип переменной.

## <a name="syntax"></a>Синтаксис

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиками символов в качестве базового класса для любого типа, который можно определить во время выполнения. Это только для управляемого кода.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс представляет базовый класс, из которого могут быть производными более специализированные интерфейсы.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Этот интерфейс не предоставляет никаких методов, кроме тех, которые унаследованы от `IDebugField` .

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
