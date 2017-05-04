---
title: "Структура PROFILER_HEAP_OBJECT | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Структура PROFILER_HEAP_OBJECT
Представляет объекты в куче собранные [Метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Синтаксис  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;  
    union {  
        PROFILER_HEAP_OBJECT_ID objectId;  
        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;  
    USHORT flags;   
    USHORT optionalInfoCount;  
} PROFILER_HEAP_OBJECT;  
```  
  
## Члены  
  
|Элемент|Тип|Описание|  
|-------------|---------|--------------|  
|objectId|[Тип PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Идентификатор объекта кучи.|  
|externalObjectAddress|[Тип PROFILER\_EXTERNAL\_OBJECT\_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|Внешний адрес объекта, например объект C\+\+\-allocated, out кучи javascript.|  
|typeNameId|[Тип PROFILER\_HEAP\_OBJECT\_NAME\_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|Идентификатор имени типа объекта в куче, полученное из [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).  Только один из `externalObjectAddress` или `typeName` присутствует в зависимости от значения `flags`.|  
|flags|[Перечисление PROFILER\_HEAP\_OBJECT\_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Флаги, которые содержат основные сведения об объекте кучи.|  
|optionalInfoCount|USHORT|Число записей, доступных для объекта [Структура PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) кучи.|