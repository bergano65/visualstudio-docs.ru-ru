---
title: Структура PROFILER_HEAP_OBJECT_SCOPE_LIST | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1285e4efa3db8a7ec99808f5888d3dbf948e589
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830325"
---
# <a name="profilerheapobjectscopelist-structure"></a>Структура PROFILER_HEAP_OBJECT_SCOPE_LIST
Эта структура не сопоставлено только объекты-функции. Область списка представляет замыкание для функции в виде списка областей, где каждая область видимости — מבתוךע heap со списком связанного свойства, представляющий переменные в каждой заданной области. В некоторых случаях доступна имена объектов в том, что область могут быть недоступны и их индекс в список свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Тип|Описание|  
|------------|----------|-----------------|  
|count|UINT|Число областей|  
|scopes|[Тип PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Массив областей.|