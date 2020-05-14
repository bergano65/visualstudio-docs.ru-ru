---
title: TYPE_INFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713319"
---
# <a name="type_info"></a>TYPE_INFO
Эта структура определяет различные виды информации о типе поля.

## <a name="syntax"></a>Синтаксис

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Участники
 `dwKind`\
 Значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) перечисления, определяющее, как интерпретировать союз.

 `type.typeMeta`\
 (только си) Содержит [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) структуру, если `dwKind` есть `TYPE_KIND_METADATA`.

 `type.typePdb`\
 (только си) Содержит [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) структуру, если `dwKind` есть `TYPE_KIND_PDB`.

 `type.typeBuilt`\
 (только си) Содержит [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) структуру, если `dwKind` есть `TYPE_KIND_BUILT`.

 `type.unused`\
 Неиспользованная обивка.

 `type`\
 Название союза.

 `unionmember`\
 (Только для C) Маршал это к соотвествуя типу структуры основанному на `dwKind`.

## <a name="remarks"></a>Примечания
 Эта структура передается методу [GetTypeInfo,](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) где она заполняется. То, как интерпретируется содержимое `dwKind` структуры, основано на поле.

> [!NOTE]
> (только си) Если `dwKind` `TYPE_KIND_BUILT`равен, то необходимо освободить основной объект [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) при разрушении `TYPE_INFO` структуры. Это выполняется с помощью вызова метода `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 (Только для C) В следующей таблице показано, как интерпретировать `unionmember` участника для каждого типа. Пример показывает, как это делается для одного типа.

|`dwKind`|`unionmember`интерпретируется как|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Пример
 В этом примере `unionmember` показано, `TYPE_INFO` как интерпретировать члена структуры в C. Этот пример показывает интерпретацию`TYPE_KIND_METADATA`только одного типа (), но другие интерпретируются точно так же.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
