---
title: "Метод IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo
Освобождает [Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) указанные структуры и связанные с ними элементы [Структура PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).  
  
## Синтаксис  
  
```  
HRESULT FreeObjectAndOptionalInfo (  
    [in] ULONG celt,  
    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
  
```  
  
#### Параметры  
 `celt`  
 Количество объектов в свободену.  
  
 `heapObjects`  
 Массив структур [Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).  
  
## Возвращаемое значение  
 HRESULT.