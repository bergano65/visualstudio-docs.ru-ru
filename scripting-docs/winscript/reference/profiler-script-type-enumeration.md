---
title: Перечисление PROFILER_SCRIPT_TYPE | Документация Майкрософт
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
ms.openlocfilehash: ac387af4601ff822982c10e61f9813b2db7e8047
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086914"
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
  
## <a name="members"></a>Члены  
  
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