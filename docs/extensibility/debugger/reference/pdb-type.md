---
title: PDB_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f14537a7543528be7ab026e7d24b9a1e9d964d0b
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460856"
---
# <a name="pdbtype"></a>PDB_TYPE

Эта структура указывает сведения о типом поля, взятое из PDB-символов.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Участники

`ulAppDomainID`\

Идентификатор приложения, от которого поступило символа. Это используется для уникальной идентификации экземпляра приложения.

`guidModule`\

Идентификатор GUID модуля, содержащего это поле.

`symid`\

Идентификатор символ, соответствующий этому полю.

## <a name="remarks"></a>Примечания

Эта структура является частью объединения в [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структуры, когда `dwKind` поле `TYPE_INFO` структура присваивается `TYPE_KIND_PDB` (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Перечисление).

## <a name="requirements"></a>Требования

Заголовок: sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
