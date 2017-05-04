---
title: "Константы, перечисления и структуры профилировщика активных скриптов | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Константы, перечисления и структуры профилировщика активных скриптов
Следующие интерфейсы используются перечисления профилировщика активного сценария.  
  
## Константы, перечисления и структуры  
  
|Константы|Описание|  
|---------------|--------------|  
|[Тип PROFILER\_EXTERNAL\_OBJECT\_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|Внешний адрес объекта профилировщика.  Используется в [Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) и [Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Тип PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Идентификатор объекта кучи.  Используется в [Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)[Структура PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [Структура PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) и [Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Тип PROFILER\_HEAP\_OBJECT\_NAME\_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|Идентификатор имени объекта кучи.  Используется в [Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Перечисления|Описание|  
|------------------|--------------|  
|[Перечисление PROFILER\_EVENT\_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Указывает типы событий, которые должны быть профилированы.|  
|[Перечисление PROFILER\_HEAP\_ENUM\_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Флаги, которые представляют, предоставляется ли дополнительная информацию об объекте кучи, на который указывает указатель в объектном отношении.  Используется в [Метод IActiveScriptProfilerControl5::EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Перечисление PROFILER\_HEAP\_OBJECT\_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Пометить, представляющий основные сведения об объекте кучи.  Используется в [Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Перечисление PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Представляет различные типы дополнительных сведений.  Используется в [Структура PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Перечисление PROFILER\_RELATIONSHIP\_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Представляет сведения об объекте в связи.  Используется в [Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Перечисление PROFILER\_SCRIPT\_TYPE](../../winscript/reference/profiler-script-type-enumeration.md)|Определяет тип скрипта.|  
  
|Структуры|Описание|  
|---------------|--------------|  
|[Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Представляет объекты кучи собранные [Метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Структура PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Представляет дополнительные сведения об объектах кучи.|  
|[Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Представляет связь объекта кучи.|  
|[Структура PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Представляет список связей, которые принадлежат объекту кучи.|  
|[Структура PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Эта структура связана с объектами функций.  Список области представляет замыкание для функции как список областей, каждая область объект кучи с сопоставленным списком свойства, представляющий переменные в каждой заданной области.  В некоторых случаях имена объектов в этой области, могут оказаться недоступными, только их идентификаторов.|  
  
## См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)