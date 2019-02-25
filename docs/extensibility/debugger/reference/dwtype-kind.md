---
title: dwTYPE_KIND | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a33bdf1875426898a6db72831bee4d1d7ac1f9a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689256"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Указывает, как интерпретировать тип [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта.

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

#### <a name="parameters"></a>Параметры
TYPE_KIND_METADATA [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) объединения должны интерпретироваться как [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) структуры.

TYPE_KIND_PDB `TYPE_INFO` объединения должны интерпретироваться как [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) структуры.

TYPE_KIND_BUILT `TYPE_INFO` объединения должны интерпретироваться как [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) структуры.

## <a name="remarks"></a>Примечания
Значения этого перечисления отображаются в `dwKind` поле [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структурировать и используются для определения интерпретации `type` члена объединения. `TYPE_INFO` Структура возвращается путем вызова [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) метод.

## <a name="requirements"></a>Требования
Заголовок: sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
