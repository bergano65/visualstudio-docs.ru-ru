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
ms.openlocfilehash: f7230e65e5559d53e56cf6424a34dd44aa4edda7
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150937"
---
# <a name="profilereventmask-enumeration"></a>Перечисление PROFILER_EVENT_MASK
Указывает типы событий, которые должны быть профилированы.  
  
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
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Профили функции, которые определены в скрипт, написанный пользователем и динамического кода.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Профили собственных функций, определенных обработчиком сценариев.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Профили всех функций подсистемы определяемых пользователем и сценариев, за исключением вызовов в объектной модели документа (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Профили функций, которые вызывают в модель DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Профилирует все функции, включая вызовы в модель DOM.|  
  
## <a name="see-also"></a>См. также  
 [Активных скриптов Profiler константы, перечисления и структуры](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)