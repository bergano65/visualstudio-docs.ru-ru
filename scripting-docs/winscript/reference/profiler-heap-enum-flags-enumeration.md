---
title: "Перечисление PROFILER_HEAP_ENUM_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Перечисление PROFILER_HEAP_ENUM_FLAGS
Флаги, которые представляют, предоставляется ли дополнительная информацию об объекте кучи, на который указывает указатель в объектном отношении.  Используется в методе [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).  
  
## Синтаксис  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,  
} PROFILER_HEAP_ENUM_FLAGS;  
  
```  
  
## Члены  
  
|Элемент|Значение|Описание|  
|-------------|--------------|--------------|  
|PROFILER\_HEAP\_ENUM\_FLAGS\_NONE|0x00000000|Этот объект кучи не предоставляет дополнительные сведения о связи объекта.  Этот объект кучи ведет себя так же, как [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER\_HEAP\_ENUM\_ENUM\_ STORE\_RELATIONSHIP\_FLAGS|0x00000001|Этот объект кучи предоставляет сведения о ли указанный объект в связи объекта в метод получения или установки.  Эти сведения будут сохраняться в максимуме 2 байт \(16 бит\) поля [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) как одно из значений перечисления [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md).|