---
title: Константы, перечисления и структуры в профилировщике активных скриптов | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a9409799c7da2ed3f4864dea0e7785635492220
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572690"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Константы, перечисления и структуры профилировщика активных скриптов
В интерфейсах профилировщика активных скриптов используются следующие перечисления.  
  
## <a name="constants-enumerations-and-structures"></a>Константы, перечисления и структуры  
  
|Константы|Описание|  
|---------------|-----------------|  
|[Тип PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|Адрес внешнего объекта профилировщика. Используется в [структуре PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) и [структуре PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Тип PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Идентификатор объекта кучи. Используется в структуре [PROFILER_HEAP_OBJECT Structure](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), структура [PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)и [Структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Тип PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|Идентификатор имени объекта кучи. Используется в [структуре PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Перечисления|Описание|  
|------------------|-----------------|  
|[Перечисление PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Указывает типы событий, для которых необходимо выполнить профилирование.|  
|[Перечисление PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Флаги, которые указывают, предоставляются ли дополнительные сведения об объекте кучи, на который указывает связь объекта. Используется в [методе IActiveScriptProfilerControl5:: EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Перечисление PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Флаги, представляющие основные сведения об объекте кучи. Используется в [структуре PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Перечисление PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Представляет различные типы необязательных сведений. Используется в [структуре PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Перечисление PROFILER_RELATIONSHIP_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Представляет сведения об объекте в связи. Используется в [структуре PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Перечисление PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md)|Задает тип скрипта.|  
  
|Структуры|Описание|  
|----------------|-----------------|  
|[Структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Представляет объекты кучи, собранные [методом метод iactivescriptprofilercontrol3:: EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Представляет необязательные сведения об объектах кучи.|  
|[Структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Представляет связь объекта кучи.|  
|[Структура PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Представляет список связей, принадлежащих объекту кучи.|  
|[Структура PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Эта структура связана только с объектами функций. Список область представляет замыкание функции в виде списка областей, где каждая область является объектом кучи со связанным списком свойств, представляющим переменные в каждой заданной области. В некоторых случаях имена объектов в этой области могут быть недоступны, только их идентификаторы.|  
|[Структура PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Представляет сведения о типе подстроки.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)