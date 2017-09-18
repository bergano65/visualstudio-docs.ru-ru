---
title: "BP_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION"
helpviewer_keywords: 
  - "Объединение BP_LOCATION"
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BP_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает тип структуры, используемый для описания расположения точки останова.  
  
## Синтаксис  
  
```cpp#  
typedef struct _BP_LOCATION {  
   BP_LOCATION_TYPE bpLocationType;  
   union {  
      BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;  
      BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;  
      BP_LOCATION_CODE_CONTEXT     bplocCodeContext;  
      BP_LOCATION_CODE_STRING      bplocCodeString;  
      BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;  
      BP_LOCATION_DATA_STRING      bplocDataString;  
      BP_LOCATION_RESOLUTION       bplocResolution;  
      DWORD                        unused;  
   } bpLocation;  
} BP_LOCATION;  
```  
  
```c#  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## Члены  
 `bpLocationType`  
 Значение [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) перечисление, используемое для интерпретации  `bpLocation` объединение или  `unionmemberX` члены.  
  
 `bpLocation`.`bplocCodeFileLine`  
 \[C\+\+ содержит только\] [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) если структура  `bpLocationType` \=  `BPLT_CODE_FILE_LINE`.  
  
 `bpLocation.bplocCodeFuncOffset`  
 \[C\+\+ содержит только\] [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) если структура  `bpLocationType` \=  `BPLT_CODE_FUNC_OFFSET`.  
  
 `bpLocation.bplocCodeContext`  
 \[C\+\+ содержит только\] [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) если структура  `bpLocationType` \=  `BPLT_CODE_CONTEXT`.  
  
 `bpLocation.bplocCodeString`  
 \[C\+\+ содержит только\] [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) если структура  `bpLocationType` \=  `BPLT_CODE_STRING`.  
  
 `bpLocation.bplocCodeAddress`  
 \[C\+\+ содержит только\] [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) если структура  `bpLocationType` \=  `BPLT_CODE_ADDRESS`.  
  
 `bpLocation.bplocDataString`  
 \[C\+\+ содержит только\] [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) если структура  `bpLocationType` \=  `BPLT_DATA_STRING`.  
  
 `bpLocation.bplocResolution`  
 \[C\+\+ содержит только\] [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) если структура  `bpLocationType` \=  `BPLT_RESOLUTION`.  
  
 `unionmember1`  
 \[C\#\] только на способ интерпретации см. в разделе " примечания ".  
  
 `unionmember2`  
 \[C\#\] только на способ интерпретации см. в разделе " примечания ".  
  
 `unionmember3`  
 \[C\#\] только на способ интерпретации см. в разделе " примечания ".  
  
 `unionmember4`  
 \[C\#\] только на способ интерпретации см. в разделе " примечания ".  
  
## Заметки  
 Эта структура элемент [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и  [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
 Только \[c\#\] `unionmemberX` члены, интерпретируются согласно следующей таблице.  Просмотрите вниз с левого столбца, `bpLocationType` вид, что через другие столбцы задает значение затем что каждое  `unionmemberX` член представляет и маршалирует  `unionmemberX` соответственно.  См. пример для способа интерпретации части этой структуры в c\#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` \(контекст\)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|\-|\-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` \(контекст\)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|\-|\-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPLT_CODE_STRING`|`string` \(контекст\)|`string` \(условное выражение\)|\-|\-|  
|`BPLT_CODE_ADDRESS`|`string` \(контекст\)|`string` \(URL\-адрес модуля\)|`string` \(имя функции\)|`string` \(адрес\)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` \(контекст\)|`string` \(expression\)|`uint` \(число элементов\)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|\-|\-|\-|  
  
## Пример  
 В этом примере показано, как интерпретировать `BP_LOCATION` структура в c\# для  `BPLT_DATA_STRING` этот тип.  Этот конкретный тип показано, как интерпретировать все 4 `unionmemberX` элементы всех возможных форматов \(объекте, строку и номер\).  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_LOCATION bp)  
        {  
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)  
            {  
                 IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
                 string context = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);  
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
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)