---
title: BP_RESOLUTION_LOCATION | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 473487acef459f35d2c04d92e0e0861aa8f3cd85
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258327"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает структуру разрешения расположения точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>Участники  
 `bpType`  
 Значение из [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) перечисление, указывающее способ интерпретации `bpResLocation` объединение или `unionmemberX` членов.  
  
 `bpResLocation.bpresCode`  
 [C++] Содержит [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) структуры, если `bpType`  =  `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 [C++] Содержит [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) структуры, если `bpType`  =  `BPT_DATA`.  
  
 `bpResLocation.unused`  
 [C++] Заполнитель.  
  
 `unionmember1`  
 [Только для C#] См. в разделе "Примечания" о том, как интерпретировать.  
  
 `unionmember2`  
 [Только для C#] См. в разделе "Примечания" о том, как интерпретировать.  
  
 `unionmember3`  
 [Только для C#] См. в разделе "Примечания" о том, как интерпретировать.  
  
 `unionmember4`  
 [Только для C#] См. в разделе "Примечания" о том, как интерпретировать.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является членом [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) и [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структуры.  
  
 [Только для C#] `unionmemberX` Члены интерпретируются согласно следующей таблице. Найдите в левом столбце для `bpType` поперек затем значение с целью определить, о том, что `unionmemberX` представляет член и marshal `unionmemberX` соответствующим образом. См. в примере способ интерпретации этой структуры в C#.  
  
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
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)

