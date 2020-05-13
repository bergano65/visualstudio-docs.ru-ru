---
title: dwTYPE_KIND Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737192"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Определяет, как интерпретировать тип объекта [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>Поля
`TYPE_KIND_METADATA`\
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) союз следует интерпретировать как [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) структуру.

`TYPE_KIND_PDB`\
Профсоюз `TYPE_INFO` следует интерпретировать как [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) структуру.

`TYPE_KIND_BUILT`\
Профсоюз `TYPE_INFO` следует интерпретировать как [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) структуру.

## <a name="remarks"></a>Примечания
Значения этого перечисления отображаются в `dwKind` поле структуры [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) и используются `type` для определения интерпретации члена профсоюза. Структура `TYPE_INFO` возвращается по вызову к методу [GetTypeInfo.](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)

## <a name="requirements"></a>Требования
Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
