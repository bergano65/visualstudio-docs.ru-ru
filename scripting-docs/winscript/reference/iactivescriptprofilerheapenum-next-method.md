---
title: "IActiveScriptProfilerHeapEnum::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::Next
Возвращает следующий объект или объекты в наборе возражают из кучи [Метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Синтаксис  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,   
    [out] ULONG *pceltFetched);  
  
```  
  
#### Параметры  
 `celt`  
 Число возвращаемых объектов.  
  
 `heapObjects`  
 \[out\] следующие структуры [Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).  
  
 `pceltFetched`  
 \[out\] количество объектов, возвращенных  
  
## Возвращаемое значение  
 HRESULT.