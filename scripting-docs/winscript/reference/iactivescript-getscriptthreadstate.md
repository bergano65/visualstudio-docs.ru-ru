---
title: "IActiveScript::GetScriptThreadState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadState"
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadState
Получает текущее состояние потока скрипта.  
  
## Синтаксис  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### Параметры  
 `stidThread`  
 \[in\] идентификатор потока, для которого нужно получить состояние или один из следующих специальных идентификаторов потока:  
  
|Значение|Значение|  
|--------------|--------------|  
|SCRIPTTHREADID\_BASE|Базовый поток. то есть поток, в котором был создан экземпляр обработчика сценариев.|  
|SCRIPTTHREADID\_CURRENT|Выполняющийся в данный момент поток.|  
  
 `pstsState`  
 \[out\] адрес переменной, которая получает состояние указанного потока.  Состояние отображается один из именованных постоянных значений, заданных перечислением [Перечисление SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md).  Если этот параметр не задает текущий поток, состояние может измениться в любой момент.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов еще не был загружен или не был инициализирован\).|  
  
## Заметки  
 Этот метод может быть вызван из потоков, не относящихся к базовому без привести к появлению выноски отличные от причины для размещения объектов или к интерфейсу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)