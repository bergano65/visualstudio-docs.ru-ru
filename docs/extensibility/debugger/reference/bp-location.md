---
title: BP_LOCATION | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b73a625e21da8e8ba026df140e437e96bdeb1ff5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bplocation"></a>BP_LOCATION
Указывает тип структуры, используемый для описания расположение точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
  
```csharp  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## <a name="members"></a>Участники  
 `bpLocationType`  
 Значение из [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) перечисление, используемое для интерпретации `bpLocation` union или `unionmemberX` члены.  
  
 `bpLocation`.`bplocCodeFileLine`  
 [C++] Содержит [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) структуры, если `bpLocationType`  =  `BPLT_CODE_FILE_LINE`.  
  
 `bpLocation.bplocCodeFuncOffset`  
 [C++] Содержит [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) структуры, если `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`.  
  
 `bpLocation.bplocCodeContext`  
 [C++] Содержит [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) структуры, если `bpLocationType`  =  `BPLT_CODE_CONTEXT`.  
  
 `bpLocation.bplocCodeString`  
 [C++] Содержит [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) структуры, если `bpLocationType`  =  `BPLT_CODE_STRING`.  
  
 `bpLocation.bplocCodeAddress`  
 [C++] Содержит [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) структуры, если `bpLocationType`  =  `BPLT_CODE_ADDRESS`.  
  
 `bpLocation.bplocDataString`  
 [C++] Содержит [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) структуры, если `bpLocationType`  =  `BPLT_DATA_STRING`.  
  
 `bpLocation.bplocResolution`  
 [C++] Содержит [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) структуры, если `bpLocationType`  =  `BPLT_RESOLUTION`.  
  
 `unionmember1`  
 [Только в C#] См. заметки о том, как интерпретировать.  
  
 `unionmember2`  
 [Только в C#] См. заметки о том, как интерпретировать.  
  
 `unionmember3`  
 [Только в C#] См. заметки о том, как интерпретировать.  
  
 `unionmember4`  
 [Только в C#] См. заметки о том, как интерпретировать.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является членом [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
 [Только в C#] `unionmemberX` Члены, интерпретируются согласно следующей таблице. Найдите в левом столбце для `bpLocationType` значение затем найдите в других столбцах для определения содержимого каждого `unionmemberX` представляет член и marshal `unionmemberX` соответствующим образом. Далее приведен пример способ интерпретации часть этой структуры в C#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` (контекст)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` (контекст)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPLT_CODE_STRING`|`string` (контекст)|`string` (условное выражение)|-|-|  
|`BPLT_CODE_ADDRESS`|`string` (контекст)|`string` (модуль URL-адрес)|`string` (имя функции)|`string` (адрес)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (контекст)|`string` (выражение данных)|`uint` (число элементов)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|  
  
## <a name="example"></a>Пример  
 В этом примере показано, как интерпретировать `BP_LOCATION` структуры в C# для `BPLT_DATA_STRING` типа. Этот конкретный тип показано, как интерпретировать все четыре `unionmemberX` члены все возможные форматы (объекта, строки и номер).  
  
```csharp  
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
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)