---
title: "Перечисление PROFILER_SCRIPT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_SCRIPT_TYPE
apilocation: scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Перечисление PROFILER_SCRIPT_TYPE
Указывает тип скрипта.  
  
## Синтаксис  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## Члены  
  
|Элемент|Описание|  
|-------------|--------------|  
|PROFILER\_SCRIPT\_TYPE\_USER|Определяет пользователь\- код скрипта.|  
|PROFILER\_SCRIPT\_TYPE\_DYNAMIC|Указывает код скрипта, создаваемый динамически во время выполнения.|  
|PROFILER\_SCRIPT\_TYPE\_NATIVE|Указывает тип скрипта для собственных функций и объектов, определенных обработчиком скриптов.|  
|PROFILER\_SCRIPT\_TYPE\_DOM|Определяет вызов в объектной модели документов \(DOM\) Internet Explorer, например вызова метода `document.getElementById`.|  
  
## См. также  
 [Константы, перечисления и структуры профилировщика активных скриптов](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)