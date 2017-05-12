---
title: "Структура PROFILER_HEAP_OBJECT_RELATIONSHIP | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Структура PROFILER_HEAP_OBJECT_RELATIONSHIP
Представляет связь объектов кучи.  
  
## Синтаксис  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP  
{  
    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;  
    PROFILER_RELATIONSHIP_INFO relationshipInfo;  
    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union  
    {  
        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;  
        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;  
        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;  
        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
  
```  
  
## Члены  
  
|Элемент|Значение|Описание|  
|-------------|--------------|--------------|  
|relationshipId|[Тип PROFILER\_HEAP\_OBJECT\_NAME\_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|Имя\/идентификатор связи из [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[Перечисление PROFILER\_RELATIONSHIP\_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Сведения об отношениях.|  
|numberValue|double|Значение числа.  Установлено только одно из `numberValue`\/`stringValue`\/`objectId`\/`externalObjectAddress`, основанный на значении `relationshipInfo`.|  
|stringValue|LPCWSTR|Строковое значение.|  
|objectId|[Тип PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Идентификатор объекта кучи.|  
|externalObjectAddress|[Тип PROFILER\_EXTERNAL\_OBJECT\_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|Внешний адрес объекта.|