---
title: METADATA_ADDRESS_RETVAL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e31682de4c625e40baaac6daff4687c713abda9
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460975"
---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
Эта структура представляет значение, возвращаемое из метода или функции.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Участники
 `tokMethod`\
 Идентификатор метода это возвращаемое значение соответствует.

 `dwCorType`\
 Базовый тип возвращаемого значения. Это значение из `CorElementType` перечисление, определенное в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] файле corhdr.h пакета SDK.

 `dwSigSize`\
 Размер подписи возвращаемое значение (в `rgSig`).

 `rgSig`\
 Массив байтов, формирующие подпись возвращаемого значения.

## <a name="remarks"></a>Примечания
 Эта структура является частью объединения в [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуры, когда `dwKind` поле `DEBUG_ADDRESS_UNION` структура присваивается `ADDRESS_KIND_RETVAL` (значение из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Перечисление).

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)