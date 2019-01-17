---
title: Перечисление PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS | Документация Майкрософт
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
ms.openlocfilehash: b78285f332b339533d81228de5877043f699a67c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349144"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>Перечисление PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS
Флаги, которые представляют, является ли объект кучи указывал в объектном отношении — это метод доступа get или Set. Используется в [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) метод при PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS значение, заданное в `enumFlags` параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Значение|Описание:|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Этот объект кучи, на который указывает указатель в объектном отношении не был определен как метод получения или задания.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|Объект кучи, указанный в объектном отношении — это метод считывания. Эти сведения будут храниться в двух байтах (16 бит) из [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) поля.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|Объект кучи, указанный в объектном отношении является метод задания. Эти сведения будут храниться в двух байтах (16 бит) из `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` поля.|