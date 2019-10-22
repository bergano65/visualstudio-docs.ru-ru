---
title: Перечисление PROFILER_SCRIPT_TYPE | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574570"
---
# <a name="profiler_script_type-enumeration"></a>Перечисление PROFILER_SCRIPT_TYPE
Задает тип скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Указывает написанный пользователем код скрипта.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Указывает код скрипта, который создается динамически во время выполнения.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Указывает тип скрипта для собственных функций и объектов, определенных обработчиком скриптов.|  
|PROFILER_SCRIPT_TYPE_DOM|Указывает вызов в модель DOM (DOM) Internet Explorer, например вызов метода `document.getElementById`.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры в профилировщике Active Script](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [IActiveScriptProfilerCallback:: скрипткомпилед](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)    
 [IActiveScriptProfilerCallback2:: онфунктионентербинаме](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)