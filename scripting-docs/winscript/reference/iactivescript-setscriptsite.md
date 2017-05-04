---
title: "IActiveScript::SetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptSite"
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::SetScriptSite
Уведомляет обработчик скриптов сайта интерфейса [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) предоставленного основным приложением.  Этот метод следует вызывать прежде чем использовать другие методы интерфейса [IActiveScript](../../winscript/reference/iactivescript.md).  
  
## Синтаксис  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### Параметры  
 `pScriptSite`  
 \[in\] адрес основного приложение\- предоставленного сайта скрипта, который связывается с данным экземпляром обработчика скриптов.  Сайт должен быть уникальным присвоено данному экземпляру обработчика скриптов; ее нельзя использовать совместно с другими обработчиками скриптов.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_FAIL`|Произошла неопознанная ошибка; обработчик скриптов не смог завершить инициализации сайт.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, сайт уже был установлен\).|  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)