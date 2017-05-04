---
title: "Перечисление PROFILER_RELATIONSHIP_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Перечисление PROFILER_RELATIONSHIP_INFO
Представляет сведения об объекте в связи.  Используется в [Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## Синтаксис  
  
```  
typedef [v1_enum] enum {  
    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,  
    PROFILER_PROPERTY_TYPE_STRING = 0x02,  
    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,  
    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,  
    PROFILER_PROPERTY_TYPE_BSTR = 0x05,  
} PROFILER_RELATIONSHIP_INFO;  
  
```  
  
## Члены  
  
|Элемент|Значение|Описание|  
|-------------|--------------|--------------|  
|PROFILER\_PROPERTY\_TYPE\_NUMBER|0x01|Объект number.|  
|PROFILER\_PROPERTY\_TYPE\_STRING|0x02|Объект строка.|  
|PROFILER\_PROPERTY\_TYPE\_HEAP\_OBJECT|0x03|Объект кучи.|  
|PROFILER\_PROPERTY\_TYPE\_EXTERNAL\_OBJECT|0x04|Объект является внешним по отношению, т е не на кучу для сборки мусора.|  
|PROFILER\_PROPERTY\_TYPE\_BSTR|0x05|Объект BSTR.|