---
title: "IActiveScript::GetScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadID"
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadID
Извлекает scripting\-обработчик\- указанный идентификатор потока, связанного с данным потоком Win32.  
  
## Синтаксис  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### Параметры  
 `dwWin32ThreadID` ,  
 \[in\] идентификатор потока Win32 в процессе выполнения текущего потока.  Используйте функцию [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) чтобы получить идентификатор потока, выполняющегося в настоящее время потока.  
  
 `pstidThread` ,  
 \[out\] адрес переменной, которая получает идентификатор потока скрипта, связанный с данным потоком Win32.  Интерпретация этого идентификатора выйдено на обработчик скриптов, но может быть просто копией идентификатора потока Windows.  Обратите внимание, что если поток Win32 завершается, данный идентификатор будет неопределенным и может затем быть присвоено другой поток.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов еще не был загружен или не был инициализирован\) и поэтому не был сбой.|  
  
## Заметки  
 Полученный идентификатор может использоваться в последующих вызовах методов управления выполнения потока скрипта, как метод [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md).  
  
 Этот метод может быть вызван из потоков, не относящихся к базовому без привести к появлению выноски отличные от причины для размещения объектов или к интерфейсу [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md).  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)