---
title: METADATA_ADDRESS_METHOD Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc3dd7a34e4f9a3e1b933781aeaf4e18cad7ec17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714459"
---
# <a name="metadata_address_method"></a>METADATA_ADDRESS_METHOD
Эта структура представляет адрес метода класса.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagMETADATA_ADDRESS_METHOD {
   _mdToken tokMethod;
   DWORD    dwOffset;
   DWORD    dwVersion;
} METADATA_ADDRESS_METHOD;
```

```csharp
public struct METADATA_ADDRESS_METHOD {
   public int  tokMethod;
   public uint dwOffset;
   public uint dwVersion;
}
```

## <a name="members"></a>Участники
 `tokMethod`\
 Идентификатор метода.

 (К) `_mdToken` является `typedef` для 32-битного `int`.

 `dwOffset`\
 Смещение от начала класса к этому методу (может представлять смещение в vtable).

 `dwVersion`\
 Версия метода (это значение является уникальным для поставщика символов).

## <a name="remarks"></a>Примечания
 Эта структура является частью соединения в `dwKind` [структуре DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) когда `ADDRESS_KIND_METHOD` поле `DEBUG_ADDRESS_UNION` структуры устанавливается (значение от [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления).

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
