---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9d2bf87a804295a5ea8f6750ee9cd93643c53bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913014"
---
# <a name="unmanagedaddressthisrelative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Эта структура называется адрес, который задается по отношению к `this` указатель (`Me` в Visual Basic).

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

## <a name="terms"></a>Термины
 dwOffset смещение в байтах относительно базового положения (например, в начале класса vtable).

 dwBitOffset смещение (в битах) из базового положения (всегда равно 0, если ссылка на битовое поле).

 Количество битов, представляющее адрес dwBitLength (всегда равно 0, если ссылка на битовое поле).

## <a name="remarks"></a>Примечания
 Эта структура является частью объединения в [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуры, когда `dwKind` поле `DEBUG_ADDRESS_UNION` структура присваивается `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (значение из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Перечисление).

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)