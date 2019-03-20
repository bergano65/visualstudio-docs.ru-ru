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
ms.openlocfilehash: ca90a566db422d75fefc44267ffe10504bb872ce
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157442"
---
# <a name="profilerscripttype-enumeration"></a>Перечисление PROFILER_SCRIPT_TYPE
Указывает тип скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание:|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Указывает скрипт, написанный пользователем код.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Указывает код сценария, который создается динамически во время выполнения.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Указывает тип скрипта для собственных функций и объектов, определенных обработчиком сценариев.|  
|PROFILER_SCRIPT_TYPE_DOM|Задает вызов в объектной модели документа (DOM) Internet Explorer, например, вызов `document.getElementById` метод.|  
  
## <a name="see-also"></a>См. также  
 [Активных скриптов Profiler константы, перечисления и структуры](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)