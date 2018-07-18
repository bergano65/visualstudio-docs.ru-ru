---
title: Перечисление PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab542225e0238dbd40f90d9de66d43d0791e05e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734014"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>Перечисление PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS
Флаги, которые представляют ли объект кучи указывает в отношении объекта — это метод доступа get или Set. Используется в [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) метод PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS значения, заданные в `enumFlags` параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Этот объект кучи, указываемых в отношении объекта не определяется как метод setter или getter.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|Объект кучи, указанный в отношении объекта — это метод считывания. Эти сведения сохраняются в высокого уровня 2 байта (16 бит) из [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) поля.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|Объект кучи, указанный в отношении объекта — это метод задания свойства. Эти сведения сохраняются в высокого уровня 2 байта (16 бит) из `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` поля.|