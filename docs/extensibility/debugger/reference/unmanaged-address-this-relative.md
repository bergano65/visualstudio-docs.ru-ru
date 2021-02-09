---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c19109215a9e8824f1648860c39ccb33836ca93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879999"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Эта структура представляет адрес относительно `this` указателя ( `Me` в Visual Basic).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>Члены
 `dwOffset`\
 Смещение в байтах от базовой позиции (например, начало класса vtable).

 `dwBitOffset`\
 Смещение в битах от базовой позиции (всегда 0, если не ссылается на битовое поле).

 `dwBitLength`\
 Число битов, представляющих адрес (всегда 0, если не ссылается на битовое поле).

## <a name="remarks"></a>Remarks
 Эта структура является частью объединения в структуре [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , если `dwKind` поле `DEBUG_ADDRESS_UNION` структуры имеет `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` значение (Value из перечисления [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
