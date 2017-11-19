---
title: "Структура PROFILER_HEAP_OBJECT_SCOPE_LIST | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f0972faee11e15bd5d0e9a219e439df49d9672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectscopelist-structure"></a>Структура PROFILER_HEAP_OBJECT_SCOPE_LIST
Эта структура не сопоставлено только объекты функций. Область списка представляет нерабочего времени для функции как список областей, где каждая область видимости — кучи объекта со списком связанного свойства, представляющий переменные в каждой заданной области. В некоторых случаях имена объектов в области не становятся доступны и их индекс в списке свойств доступен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Тип|Описание|  
|------------|----------|-----------------|  
|count|UINT|Число областей|  
|scopes|[Тип PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Массив областей.|