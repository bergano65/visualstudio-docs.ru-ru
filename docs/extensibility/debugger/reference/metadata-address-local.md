---
title: METADATA_ADDRESS_LOCAL Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3adf9ca5f679c7a526f10b1ee6c91d50dac52d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714477"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

Эта структура представляет адрес локальной переменной в пределах области (обычно функции или метода).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>Участники

`tokMethod`\
Идентификатор метода или функции, частью которой является локальная переменная.

(К) `_mdToken` является `typedef` для 32-битного `int`.

`pLocal`\
Токен, адрес которого представляет эта структура.

`dwIndex`\
Может быть индекс этой локальной переменной в методе или функции, или какое-либо другое значение (специфическое для языка).

## <a name="remarks"></a>Примечания

Эта структура является частью соединения в `dwKind` [структуре DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) когда `ADDRESS_KIND_LOCAL` поле `DEBUG_ADDRESS_UNION` структуры устанавливается (значение от [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления).

> [!WARNING]
> (только си) Если `pLocal` вы не являются недействительными, то необходимо `Release` `addr` вызвать указатель токенов (это поле в [структуре DEBUG_ADDRESS):](../../../extensibility/debugger/reference/debug-address.md)
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Требования

Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
