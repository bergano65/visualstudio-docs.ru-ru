---
title: PDB_TYPE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714107"
---
# <a name="pdb_type"></a>PDB_TYPE

Эта структура определяет информацию о типе поля, взятом из символа PDB.

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
Id приложения, из которого пришел символ. Это используется для однозначной идентификации экземпляра приложения.

`guidModule`\
GUID модуля, содержащего это поле.

`symid`\
Идентификатор символа, который соответствует этому полю.

## <a name="remarks"></a>Примечания

Эта структура появляется как часть соединения в `dwKind` [структуре TYPE_INFO,](../../../extensibility/debugger/reference/type-info.md) когда `TYPE_KIND_PDB` поле `TYPE_INFO` структуры устанавливается (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) перечисления).

## <a name="requirements"></a>Требования

Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
