---
title: BP_RESOLUTION_LOCATION Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737810"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Определяет структуру расположения разрешения точки разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Участники
`bpType`\
Значение из [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) перечисления, которое определяет, как `bpResLocation` интерпретировать `unionmemberX` союз или членов.

`bpResLocation.bpresCode`\
(только си) Содержит [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) структуру, если `bpType`  =  `BPT_CODE`.

`bpResLocation.bpresData`\
(только си) Содержит [структуру BP_RESOLUTION_DATA,](../../../extensibility/debugger/reference/bp-resolution-data.md) если `bpType`  =  `BPT_DATA`.

`bpResLocation.unused`\
(только си) Заполнитель.

`unionmember1`\
(Только для C) Смотрите замечания о том, как интерпретировать.

`unionmember2`\
(Только для C) Смотрите замечания о том, как интерпретировать.

`unionmember3`\
(Только для C) Смотрите замечания о том, как интерпретировать.

`unionmember4`\
(Только для C) Смотрите замечания о том, как интерпретировать.

## <a name="remarks"></a>Примечания
Эта структура является членом [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) и [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структур.

 (Только для C) Члены `unionmemberX` интерпретируются в соответствии со следующей таблицей. Посмотрите вниз левая `bpType` колонка для значения `unionmemberX` затем поперек, чтобы определить, что каждый член представляет и маршал `unionmemberX` соответственно. См. Пример для интерпретации этой структуры в C.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(выражение данных)|`string`(имя функции)|`string`(имя изображения)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Пример
В этом примере `BP_RESOLUTION_LOCATION` показано, как интерпретировать структуру в C.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
            }
        }
    }
}
```

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
