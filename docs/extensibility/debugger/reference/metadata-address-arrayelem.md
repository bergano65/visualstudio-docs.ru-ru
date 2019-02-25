---
title: METADATA_ADDRESS_ARRAYELEM | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b08d3d25912123d62de9a096b810f42d1418aa6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707904"
---
# <a name="metadataaddressarrayelem"></a>METADATA_ADDRESS_ARRAYELEM

Эта структура представляет элемент массива в массив.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {
    _mdToken tokMethod;
    DWORD    dwIndex;
} METADATA_ADDRESS_ARRAYELEM;
```

```csharp
public struct METADATA_ADDRESS_ARRAYELEM {
    public int  tokMethod;
    public uint dwIndex;
}
```

## <a name="terms"></a>Термины

tokMethod

Идентификатор массива, этот элемент является частью.

[C++] `_mdToken` — `typedef` для 32-разрядных `int`.

dwIndex

Индекс этого элемента в массиве.

## <a name="remarks"></a>Примечания
Эта структура является частью объединения в [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуры, когда `dwKind` поле `DEBUG_ADDRESS_UNION` структура присваивается `ADDRESS_KIND_ARRAYELEM` (значение из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Перечисление).

## <a name="requirements"></a>Требования
Заголовок: sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)