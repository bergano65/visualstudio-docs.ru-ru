---
title: "BP_RESOLUTION_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_RESOLUTION_LOCATION"
helpviewer_keywords: 
  - "Структура BP_RESOLUTION_LOCATION"
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет структуру разрешения расположения точки останова.  
  
## Синтаксис  
  
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
  
```c#  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## Члены  
 `bpType`  
 Значение [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) перечисление, которое определяет, как интерпретировать  `bpResLocation` объединение или  `unionmemberX` члены.  
  
 `bpResLocation.bpresCode`  
 \[C\+\+ содержит только\] [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) если структура  `bpType` \=  `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 \[C\+\+ содержит только\] [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) если структура  `bpType` \=  `BPT_DATA`.  
  
 `bpResLocation.unused`  
 \[C\+\+\] только прототип a.  
  
 `unionmember1`  
 \[C\#\] только на способ интерпретации см. в разделе " примечания ".  
  
 `unionmember2`  
 \[C\#\] только на способ интерпретации см. в разделе " примечания ".  
  
 `unionmember3`  
 \[C\#\] только на способ интерпретации см. в разделе " примечания ".  
  
 `unionmember4`  
 \[C\#\] только на способ интерпретации см. в разделе " примечания ".  
  
## Заметки  
 Эта структура элемент [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) и  [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структуры.  
  
 Только \[c\#\] `unionmemberX` члены, интерпретируются согласно следующей таблице.  Просмотрите вниз с левого столбца, `bpType` значение затем поперек для указания того, что каждое  `unionmemberX` член представляет и маршалирует  `unionmemberX` соответственно.  См. пример для способа интерпретации эта структура в c\#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPT_DATA`|`string` \(expression\)|`string` \(имя функции\)|`string` \(имя образа\)|`enum_BP_RES_DATA_FLAGS`|  
  
## Пример  
 В этом примере показано, как интерпретировать `BP_RESOLUTION_LOCATION` структура в c\#.  
  
```c#  
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
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)