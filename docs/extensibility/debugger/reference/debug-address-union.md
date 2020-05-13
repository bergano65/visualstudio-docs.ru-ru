---
title: DEBUG_ADDRESS_UNION Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737525"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Описывает различные виды адресов.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Участники
`dwKind`\
Значение из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления, с указанием, как интерпретировать союз.

`addr.addrNative`\
(только си) Содержит структуру `dwKind` [NATIVE_ADDRESS,](../../../extensibility/debugger/reference/native-address.md) если ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
(только си) Содержит[структуру UNMANAGED_ADDRESS_THIS_RELATIVE,](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) если `dwKind` ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
(только си) Содержит структуру `dwKind` [UNMANAGED_ADDRESS_PHYSICAL,](../../../extensibility/debugger/reference/unmanaged-address-physical.md) если ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
(только си) Содержит структуру `dwKind` [METADATA_ADDRESS_METHOD,](../../../extensibility/debugger/reference/metadata-address-method.md) если ADDRESS_KIND_METHOD.

`addr.addrField`\
(только си) Содержит структуру `dwKind` [METADATA_ADDRESS_FIELD,](../../../extensibility/debugger/reference/metadata-address-field.md) если ADDRESS_KIND_FIELD.

`addr.addrLocal`\
(только си) Содержит[структуру METADATA_ADDRESS_LOCAL,](../../../extensibility/debugger/reference/metadata-address-local.md) если `dwKind` ADDRESS_KIND_LOCAL.

`addr.addrParam`\
(только си) Содержит структуру `dwKind` [METADATA_ADDRESS_PARAM,](../../../extensibility/debugger/reference/metadata-address-param.md) если ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
(только си) Содержит структуру `dwKind` [METADATA_ADDRESS_ARRAYELEM,](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) если ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
(только си) Содержит структуру `dwKind` [METADATA_ADDRESS_RETVAL,](../../../extensibility/debugger/reference/metadata-address-retval.md) если ADDRESS_KIND_RETVAL.

`addr.unused`\
Только обивка.

`addr`\
(только си) Название союза.

`unionmember`\
(Только для C) Это значение должно быть marshaled к соответствующему типу структуры на `dwKind`основе . Смотрите Замечания для `dwKind` связи между и интерпретации союза.

## <a name="remarks"></a>Примечания
Эта структура является частью [структуры DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) и представляет собой один `DEBUG_ADDRESS` из нескольких различных видов адресов (структура заполняется вызовом к методу [GetAddress).](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)

 (Только для C) В следующей таблице показано, как интерпретировать `unionmember` участника для каждого вида адреса. Пример показывает, как это делается для одного вида адреса.

|`dwKind`|`unionmember`интерпретируется как|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Пример
В этом примере показано, как`METADATA_ADDRESS_ARRAYELEM`интерпретировать `DEBUG_ADDRESS_UNION` один вид адреса () структуры в C. Остальные элементы можно интерпретировать точно так же.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
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
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
