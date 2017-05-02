---
title: "Константы SCRIPTTHREADID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADID"
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Константы SCRIPTTHREADID
Используемый, чтобы определить тип потока.  
  
## Синтаксис  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## Константы  
  
|Константа|Значение|Значение|  
|---------------|--------------|--------------|  
|SCRIPTTHREADID\_CURRENT|0xFFFFFFFD|Выполняющийся в данный момент поток.|  
|SCRIPTTHREADID\_BASE|0xFFFFFFFE|Базовый поток. то есть поток, в котором был создан экземпляр обработчика сценариев.|  
|SCRIPTTHREADID\_ALL|0xFFFFFFFF|Все потоки.|  
  
## Заметки  
 Тип `SCRIPTTHREADID` используется `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState` и `IActiveScript::InterruptScriptThread`, но только константы могут использоваться `IActiveScript::GetScriptThreadState` и `IActiveScript::InterruptScriptThread`.  
  
## См. также  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)