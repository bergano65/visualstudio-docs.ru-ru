---
title: DEBUG_ADDRESS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737520"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Эта структура представляет адрес.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>Участники
`ulAppDomainID`\
Идентификатор процесса.

`guidModule`\
GUID модуля, содержащего этот адрес.

`tokClass`\
Токен, определяющий класс или тип этого адреса.

> [!NOTE]
> Это значение характерно для поставщика символов и поэтому не имеет общего значения, кроме как идентификатор для типа класса.

`addr`\
Структура [DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) которая содержит объединение структур, описывающие индивидуальные типы адресов. Значение `addr`.`dwKind` происходит от [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления, в котором объясняется, как интерпретировать союз.

## <a name="remarks"></a>Примечания
Эта структура передается методу [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) для заполнения.

**Предупреждение только с КИ**

Если `addr.dwKind` `ADDRESS_KIND_METADATA_LOCAL` это `addr.addr.addrLocal.pLocal` и если это не нулевое значение, то вы должны вызвать `Release` указатель токенов:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Требования
Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
