---
title: Перечисление PROFILER_SCRIPT_TYPE | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734124"
---
# <a name="profilerscripttype-enumeration"></a>Перечисление PROFILER_SCRIPT_TYPE
Указывает тип сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
|PROFILER_SCRIPT_TYPE_USER|Указывает скрипт, написанный пользователем код.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Указывает код сценария, который создается динамически во время выполнения.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Указывает тип скрипта для собственных функций и объектов, определенных обработчиком сценариев.|  
|PROFILER_SCRIPT_TYPE_DOM|Задает вызов в объектной модели документа (DOM) Internet Explorer, например, вызов `document.getElementById` метод.|  
  
## <a name="see-also"></a>См. также  
 [Константы профилировщика активных скриптов, перечисления и структуры](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)