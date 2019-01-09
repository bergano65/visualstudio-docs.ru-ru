---
title: Структура PROFILER_HEAP_OBJECT_SCOPE_LIST | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 114b1a55fce34908c4274877583164aff4ec8dba
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088573"
---
# <a name="profilerheapobjectscopelist-structure"></a>Структура PROFILER_HEAP_OBJECT_SCOPE_LIST
Эта структура не сопоставлено только объекты-функции. Область списка представляет замыкание для функции в виде списка областей, где каждая область видимости — מבתוךע heap со списком связанного свойства, представляющий переменные в каждой заданной области. В некоторых случаях доступна имена объектов в том, что область могут быть недоступны и их индекс в список свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Тип|Описание|  
|------------|----------|-----------------|  
|count|UINT|Число областей|  
|scopes|[Тип PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Массив областей.|