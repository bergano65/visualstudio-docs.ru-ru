---
title: "Структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO
Представляет дополнительные сведения об объектах кучи.  
  
## Синтаксис  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO  
{  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;  
    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union  
    {  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;  
    };  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
  
```  
  
## Члены  
  
|Элемент|Тип|Описание|  
|-------------|---------|--------------|  
|infoType|[Перечисление PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Тип дополнительного сведения.|  
|прототип|[Тип PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Идентификатор объекта заполнителя объекта в куче.|  
|functionName|LPCWSTR|Имя функции объекта в куче.|  
|elementAttributesSize|UINT|Размер кучи атрибутов объектного элемента.|  
|elementTextChildrenSize|UINT|Размер дочерних элементов текст объекта в куче.|  
|scopeList|[Структура PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Список области объекта в куче.|  
|internalProperty|[Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Свойство объекта в куче внутреннее.|  
|namePropertyList|[Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Список свойств имени объекта в куче.|  
|indexPropertyList|[Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Список свойств индекса объекта в куче.|  
|relationshipList|[Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Список отношений объекта в куче.|  
|eventList|[Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Список событий объекта в куче.|