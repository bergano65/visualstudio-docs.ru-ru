---
title: DEBUG_ADDRESS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc25fb53db918486029e931a06a9e2de37f81c5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346309"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
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
Идентификатор GUID модуля, содержащего этот адрес.

`tokClass`\
Токен, идентифицирующий класс или тип этого адреса.

> [!NOTE]
> Это значение относится к поставщика символов и поэтому не имеет общие значения отличное от как идентификатор для типа класса.

`addr`\
Объект [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуру, которая содержит объединение структур, которые описывают типы отдельных адресов. Значение `addr`.`dwKind` поступает из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления, который объясняет, как интерпретировать объединение.

## <a name="remarks"></a>Примечания
Эта структура передается [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) метод для заполнения.

**Предупреждение [C++ только]**

Если `addr.dwKind` — `ADDRESS_KIND_METADATA_LOCAL` и если `addr.addr.addrLocal.pLocal` не имеет значение null, то нужно вызвать `Release` маркеров указателя:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Требования
Заголовок: sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
