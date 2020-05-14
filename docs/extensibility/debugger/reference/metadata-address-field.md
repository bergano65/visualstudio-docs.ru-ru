---
title: METADATA_ADDRESS_FIELD Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe9901ac9dab4a1ec4b5e8467f3063845dfb74f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714534"
---
# <a name="metadata_address_field"></a>METADATA_ADDRESS_FIELD

Эта структура представляет адрес поля класса или структуры.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagMETADATA_ADDRESS_FIELD {
    _mdToken tokField;
} METADATA_ADDRESS_FIELD
```

```csharp
public struct METADATA_ADDRESS_FIELD {
    public int tokField;
}
```

## <a name="members"></a>Участники

`tokField`\
Идентификатор маркера поля.

(К) `_mdToken` является `typedef` для 32-битного `int`.

## <a name="remarks"></a>Примечания

Эта структура является частью соединения в `dwKind` [структуре DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) когда `ADDRESS_KIND_FIELD` поле `DEBUG_ADDRESS_UNION` структуры устанавливается (значение от [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления).

## <a name="requirements"></a>Требования

Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
