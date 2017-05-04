---
title: "Перечисление PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Перечисление PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS
Флаги, которые представляют, является ли объект кучи, на который указывает указатель в объектном отношении, методом get или методом set.  Используется в методе [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) при PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS значение будет указано в параметре `enumFlags`.  
  
## Синтаксис  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
  
```  
  
## Члены  
  
|Элемент|Значение|Описание|  
|-------------|--------------|--------------|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_NONE|0x00000000|Этот объект кучи указывал на связь объекта и не был определен как метод получения или задания значения.|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_GET\_ACCESSOR|0x00010000|Объект кучи, указанный в связи объекта в метод получения.  Эти сведения будут сохраняться в максимуме 2 байт \(16 бит\) поля [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_SET\_ACCESSOR|0x00020000|Объект кучи, указанный в связи объекта в метод задания значения.  Эти сведения будут сохраняться в максимуме 2 байт \(16 бит\) поля `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo`.|