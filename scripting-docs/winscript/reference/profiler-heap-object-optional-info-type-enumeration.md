---
title: Перечисление PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fcb55f5f-ce75-4d05-9ce9-ba28c622f97d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a56b05c572ec5d91914dd046bfdfa39224a07de
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157741"
---
# <a name="profilerheapobjectoptionalinfotype-enumeration"></a>Перечисление PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE
Представляет различные типы данных необязательно. Используется в [структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE                    = 0x00000001,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME                = 0x00000002,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST                   = 0x00000003,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY            = 0x00000004,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES              = 0x00000005,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES             = 0x00000006,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE      = 0x00000007,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE   = 0x00000008,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS                = 0x00000009,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS                  = 0x0000000A,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE                    = PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS} PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Значение|Описание:|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE|0x00000001|Сведения о прототипа кучи.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME|0x00000002|Сведения об объекте кучи имени функции.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST|0x00000003|Сведения об объекте кучи [структура PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md).|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY|0x00000004|Сведения об объекте кучи внутреннее свойство.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES|0x00000005|Сведения о свойствах объекта heap имя.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES|0x00000006|Сведения о свойствах объекта heap индекса.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE|0x00000007|Размер атрибуты, связанные с элементом DOM.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE|0x00000008|Размер любой текст, связанный с элементом DOM.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS|0x00000009|Сведения о связях объекта heap.|  
|ROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS|0x0000000A|Сведения о событиях объект кучи среды выполнения Windows.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS|Максимальное значение данного перечисления.|