---
title: "Перечисление PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fcb55f5f-ce75-4d05-9ce9-ba28c622f97d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Перечисление PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE
Представляет различные типы дополнительных сведений.  Используется в [Структура PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).  
  
## Синтаксис  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE                    = 0x00000001,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME                = 0x00000002,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST                   = 0x00000003,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY            = 0x00000004,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES              = 0x00000005,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES             = 0x00000006,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE      = 0x00000007,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE   = 0x00000008,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS                = 0x00000009,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS                  = 0x0000000A,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE                    = PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE;  
  
```  
  
## Члены  
  
|Элемент|Значение|Описание|  
|-------------|--------------|--------------|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_PROTOTYPE|0x00000001|Сведения о прототипе объекта кучи.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_FUNCTION\_NAME|0x00000002|Сведения об имени функции объекта кучи.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_SCOPE\_LIST|0x00000003|Сведения о [Структура PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md) объекта кучи.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_INTERNAL\_PROPERTY|0x00000004|Сведения о свойстве кучи внутреннего объекта.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_NAME\_PROPERTIES|0x00000005|Сведения о свойствах имени объекта кучи.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_INDEX\_PROPERTIES|0x00000006|Сведения о свойствах индекса объекта кучи.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_ELEMENT\_ATTRIBUTES\_SIZE|0x00000007|Размер атрибутов, связанных с элементом модели.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_ELEMENT\_TEXT\_CHILDREN\_SIZE|0x00000008|Размер любого текста, который связан с элементом модели.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_RELATIONSHIPS|0x00000009|Сведения о связях объекта кучи.|  
|ROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_WINRTEVENTS|0x0000000A|Сведения о событиях Windows кучи среды выполнения объекта.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_MAX\_VALUE|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_WINRTEVENTS|Максимальное значение этого перечисления.|