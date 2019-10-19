---
title: Перечисление PROFILER_EVENT_MASK | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e1e7f3b604832014cb23245b105756d1126c5b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572282"
---
# <a name="profiler_event_mask-enumeration"></a>Перечисление PROFILER_EVENT_MASK
Указывает типы событий, для которых необходимо выполнить профилирование.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Функции профилей, определенные в скриптах, написанных пользователем, и в динамическом коде.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Профили собственных функций, определяемых обработчиком скриптов.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Профили всех определяемых пользователем функций механизма создания скриптов, за исключением вызовов в модель DOM (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Функции профилей, вызывающие модель DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Профили всех функций, включая вызовы модели DOM.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры в профилировщике Active Script](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [IActiveScriptProfilerControl:: сетпрофилеревентмаск](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)    
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)