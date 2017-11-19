---
title: "Перечисление PROFILER_HEAP_ENUM_FLAGS | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a7a27f4d9d7f834b07a2db5ba8433b63222a3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapenumflags-enumeration"></a>Перечисление PROFILER_HEAP_ENUM_FLAGS
Флаги, которые представляют отображением дополнительных сведений о куче объект, указанный в отношении объекта. Используется в [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Этот объект кучи не предоставляет дополнительных сведений о связи объектов. Этот объект кучи ведет себя так же, как [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Этот объект кучи будет предоставлять сведения о того, является ли объект, указанный в отношении объекта — это метод доступа get или Set. Эти сведения сохраняются в высокого уровня 2 байта (16 бит) из [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) поле как один из [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) значения перечисления.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Этот объект кучи используется для правильного отображения подстроки.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Этот объект кучи используется для правильного отображения подстроки.|