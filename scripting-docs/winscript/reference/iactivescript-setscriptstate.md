---
title: "IActiveScript::SetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptState"
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::SetScriptState
Помещает обработчик скриптов в заданном состоянии.  Этот метод может быть вызван из потоков, не относящихся к базовому без привести к появлению выноски отличные от причины для размещения объектов или к интерфейсу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## Синтаксис  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### Параметры  
 `ss`  
 \[in\] задает обработчик скриптов к заданному условию.  Может принимать одно из значений, определенных в перечислении [Перечисление SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md).  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_FAIL`|Обработчик скриптов не поддерживает вернитесь к инициализированному состояние.  Основное приложение должно отменить этот обработчик сценариев и создать, инициализировать и загрузить новый обработчик скриптов для достижения одного результата.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов еще не был загружен или не был инициализирован\) и поэтому не был сбой.|  
|`OLESCRIPT_S_PENDING`|Метод был поставлен в очередь успешно, но состояние не изменилось.  При изменениях состояния, сайт, будут Позвонитьы обратно с помощью метода [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md).|  
|`S_FALSE`|Метод выполнен успешно, но были уже скрипт в определенном состоянии.|  
  
## Заметки  
 Дополнительные сведения о состояниях обработчика скриптов см. в разделе состояний обработчика скриптов [Обработчики скриптов Windows](../../winscript/windows-script-engines.md).  
  
## См. также  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)