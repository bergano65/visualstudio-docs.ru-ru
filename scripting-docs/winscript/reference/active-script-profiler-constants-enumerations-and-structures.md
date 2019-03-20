---
title: Активных скриптов Profiler константы, перечисления и структуры | Документация Майкрософт
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
ms.openlocfilehash: 1d39e6feb2cddd0c573368db9bf50b1e77f2e48d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154729"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Константы, перечисления и структуры профилировщика активных скриптов
Следующие перечисления используются интерфейсы Profiler активных скриптов.  
  
## <a name="constants-enumerations-and-structures"></a>Константы, перечисления и структуры  
  
|Константы|Описание:|  
|---------------|-----------------|  
|[Тип PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|Адрес внешнего объекта профилировщика. Используется в [структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) и [структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Тип PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Идентификатор объекта heap. Используется в [структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)[структура PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)и [Структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Тип PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|Идентификатор имени объекта heap. Используется в [структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Перечисления|Описание:|  
|------------------|-----------------|  
|[Перечисление PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Указывает типы событий, которые должны быть профилированы.|  
|[Перечисление PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Флаги, представляющие ли предоставляется дополнительную информацию об объекте кучи, на который указывает указатель в объектном отношении. Используется в [метод IActiveScriptProfilerControl5::EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Перечисление PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Флаги, которые представляют основные сведения об объекте кучи. Используется в [структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Перечисление PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Представляет различные типы данных необязательно. Используется в [структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Перечисление PROFILER_RELATIONSHIP_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Представляет сведения об объекте в связи. Используется в [структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Перечисление PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md)|Указывает тип скрипта.|  
  
|Структуры|Описание:|  
|----------------|-----------------|  
|[Структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Представляет объекты кучи для сбора [метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Представляет Дополнительные сведения об объектах в куче.|  
|[Структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Представляет связь объекта heap.|  
|[Структура PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Представляет список связей, принадлежащих объекту кучи.|  
|[Структура PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Эта структура не сопоставлено только объекты-функции. Область списка представляет замыкание для функции в виде списка областей, где каждая область видимости — מבתוךע heap со списком связанного свойства, представляющий переменные в каждой заданной области. В некоторых случаях имена объектов в этой области могут быть недоступны, только их идентификаторы.|  
|[Структура PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Представляет сведения о типе подстроки.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)