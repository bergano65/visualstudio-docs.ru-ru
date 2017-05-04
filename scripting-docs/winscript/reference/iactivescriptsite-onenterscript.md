---
title: "IActiveScriptSite::OnEnterScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnEnterScript"
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnEnterScript
Уведомляет основное приложение о том, что обработчик скриптов был запущен выполнять код сценария.  
  
## Синтаксис  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## Возвращаемое значение  
 Возвращает значение `S_OK` в случае успеха.  
  
## Заметки  
 Обработчик скриптов, должен вызывать этот метод для каждой записи или входе в атмосферу на обработчик скриптов.  Например, если скрипт вызывает объект, который затем запускает событие обращанное обработчиком скриптов, обработчик скриптов, должен вызывать `IActiveScriptSite::OnEnterScript` до выполнения событие и должен вызвать метод [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) после выполнения событие, но перед возвратом к объекту запустившим данное событие.  Вызовы к этому методу могут быть вложенными.  Каждый вызов этого метода необходим соответствующий вызов `IActiveScriptSite::OnLeaveScript`.  
  
## См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)