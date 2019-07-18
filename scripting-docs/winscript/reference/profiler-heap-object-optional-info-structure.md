---
title: Структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c7f28499b5d6e1e01caab1e6fd83fc5ab72ccf6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823870"
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>Структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO
Представляет Дополнительные сведения об объектах в куче.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Тип|Описание|  
|------------|----------|-----------------|  
|Свойство|[Перечисление PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Тип необязательные поля.|  
|prototype|[Тип PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Идентификатор объекта heap прототип объекта.|  
|functionName|LPCWSTR|Имя функции кучи объекта.|  
|elementAttributesSize|UINT|Размер объекта heap атрибутов элемента.|  
|elementTextChildrenSize|UINT|Размер дочерних элементов объекта heap текста.|  
|scopeList|[Структура PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Объект кучи области списка.|  
|internalProperty|[Структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Внутреннее свойство объекта heap.|  
|namePropertyList|[Структура PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Список свойств name объекта heap.|  
|indexPropertyList|[Структура PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Список свойств индекса кучи объекта.|  
|relationshipList|[Структура PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Список связей объекта heap.|  
|eventList|[Структура PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Список событий объект кучи.|