---
title: "IActiveScriptSite::OnLeaveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnLeaveScript"
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnLeaveScript
Уведомляет основное приложение о том, что обработчик скриптов возвращал из выполнять код сценария.  
  
## Синтаксис  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## Возвращаемое значение  
 Возвращает значение `S_OK` в случае успеха.  
  
## Заметки  
 Обработчик скриптов, должен вызывать этот метод перед возвращением элемент управления вызывающему приложению, вошло обработчика скриптов.  Например, если скрипт вызывает объект, который затем запускает событие обращанное обработчиком скриптов, обработчик скриптов должен вызвать метод [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) до выполнения событие и должен вызвать `IActiveScriptSite::OnLeaveScript` после выполнения событие перед возвратом к объекту запустившим данное событие.  Вызовы к этому методу могут быть вложенными.  Каждый вызов `IActiveScriptSite::OnEnterScript` требуется соответствующий вызова этого метода.  
  
## См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)