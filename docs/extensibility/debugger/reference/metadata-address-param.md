---
title: METADATA_ADDRESS_PARAM Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0319cfc6f2be817a25126e67cdc470bc727a4ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714443"
---
# <a name="metadata_address_param"></a>METADATA_ADDRESS_PARAM
Эта структура представляет собой параметр метода или функции.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagMETADATA_ADDRESS_PARAM {
   _mdToken tokMethod;
   _mdToken tokParam;
   DWORD    dwIndex;
} METADATA_ADDRESS_PARAM;
```

```csharp
public struct METADATA_ADDRESS_PARAM {
   public int  tokMethod;
   public int  tokParam;
   public uint dwIndex;
}
```

## <a name="members"></a>Участники
 `tokMethod`\
 Идентификатор метода, частью которой является параметр.

 `tokParam`\
 Идентификатор параметра.

 `dwIndex`\
 Индекс параметра в списке параметров.

## <a name="remarks"></a>Примечания
 Эта структура является частью соединения в `dwKind` [структуре DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) когда `ADDRESS_KIND_PARAM` поле `DEBUG_ADDRESS_UNION` структуры устанавливается (значение от [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления).

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
