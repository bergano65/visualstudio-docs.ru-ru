---
title: "IActiveScript::GetCurrentScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetCurrentScriptThreadID"
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetCurrentScriptThreadID
Извлекает scripting\-обработчик\- указанный идентификатор выполняющегося в настоящее время потока.  Идентификатор может использоваться в последующих вызовах методов выполнение\- элемента управления потока скрипта, как метод [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md).  
  
## Синтаксис  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### Параметры  
 `pstidThread`  
 \[out\] адрес переменной, которая получает идентификатор потока скрипта, связанный с текущим потоком.  Интерпретация этого идентификатора выйдено на обработчик скриптов, но может быть просто копией идентификатора потока Windows.  Если поток Win32 завершается, данный идентификатор будет неопределенным и может затем быть присвоено другой поток.  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или `E_POINTER`, если указан недопустимый указатель.  
  
## Заметки  
 Этот метод может быть вызван из потоков, не относящихся к базовому без привести к появлению выноски отличные от причины для размещения объектов или к интерфейсу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)