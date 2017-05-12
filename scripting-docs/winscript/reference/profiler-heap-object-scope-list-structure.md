---
title: "Структура PROFILER_HEAP_OBJECT_SCOPE_LIST | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Структура PROFILER_HEAP_OBJECT_SCOPE_LIST
Эта структура сопоставитьа с объектами функции.  Список области представляет закрытие для функции, такие как список областей, где каждая область объект кучи со связанным с ним списком свойств, представляющий переменные в каждой заданной области.  В некоторых случаях имена объектов в этой области могут оказаться недоступными и только их индекс в списке свойств доступен.  
  
## Синтаксис  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];  
} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
  
```  
  
## Члены  
  
|Элемент|Тип|Описание|  
|-------------|---------|--------------|  
|count|UINT|Количество областей|  
|scopes|[Тип PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Массив областей.|