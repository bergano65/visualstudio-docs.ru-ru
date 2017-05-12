---
title: "Метод IActiveScriptProfilerHeapEnum::GetOptionalInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Метод IActiveScriptProfilerHeapEnum::GetOptionalInfo
Получает дополнительные сведения в указанном объекте \(из набора объектов кучи, возвращаемых из [Метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)\).  
  
 Не следует освободить память, присвоенную к возвращенным объектам.  Вместо этого необходимо вызвать метод [Метод IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## Синтаксис  
  
```  
HRESULT GetOptionalInfo (  
    [in] PROFILER_HEAP_OBJECT* heapObject,  
    [in] ULONG celt,  
    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
  
```  
  
#### Параметры  
 `heapObject`  
 [Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md), для которого требуется вернуть сведения.  
  
 `celt`  
 Количество структур [Структура PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md), который необходимо вернуть.  
  
 `optionalInfo`  
 \[out\] массив структур [Структура PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) для указанного объекта.  
  
## Возвращаемое значение  
 HRESULT.