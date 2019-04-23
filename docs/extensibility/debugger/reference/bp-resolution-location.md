---
title: BP_RESOLUTION_LOCATION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6de035568e1c2aebe853d25dc5f769d233da819
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662911"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
Задает структуру разрешения расположения точки останова.

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
`bpType` Значение из [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) перечисление, указывающее способ интерпретации `bpResLocation` объединение или `unionmemberX` членов.

`bpResLocation.bpresCode`

 [C++ только] Содержит [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) структуры, если `bpType`  =  `BPT_CODE`.

`bpResLocation.bpresData`

 [C++ только] Содержит [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) структуры, если `bpType`  =  `BPT_DATA`.

`bpResLocation.unused`

 [C++ только] Заполнитель.

`unionmember1`

 [C# только] См. в разделе "Примечания" о том, как интерпретировать.

`unionmember2`

 [C# только] См. в разделе "Примечания" о том, как интерпретировать.

`unionmember3`

 [C# только] См. в разделе "Примечания" о том, как интерпретировать.

`unionmember4`

 [C# только] См. в разделе "Примечания" о том, как интерпретировать.

## <a name="remarks"></a>Примечания
Эта структура является членом [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) и [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структуры.

 [C# только] `unionmemberX` Члены интерпретируются согласно следующей таблице. Найдите в левом столбце для `bpType` поперек затем значение с целью определить, о том, что `unionmemberX` представляет член и marshal `unionmemberX` соответствующим образом. См. в примере способ интерпретации этой структуры в C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (выражение данных)|`string` (имя функции)|`string` (имя образа)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Пример
В этом примере показано, как интерпретировать `BP_RESOLUTION_LOCATION` структуры в C#.

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
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
