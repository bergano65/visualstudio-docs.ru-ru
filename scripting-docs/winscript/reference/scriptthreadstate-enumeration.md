---
title: "Перечисление SCRIPTTHREADSTATE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADSTATE — перечисление"
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Перечисление SCRIPTTHREADSTATE
Задает состояние потока в обработчике скриптов.  Это перечисление используется методом [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md).  
  
## Синтаксис  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## Значения перечисления  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE\_NOTINSCRIPT|Указанный поток в настоящее время не поддерживает написанное событие, обрабатывает сразу исполненное текст скрипта или не запускает макрос скрипта.|  
|SCRIPTTHREADSTATE\_RUNNING|Указанный поток активно ведет написанное событие, обрабатывает сразу исполненное текста сценария и запускает макрос скрипта.|  
  
## См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)