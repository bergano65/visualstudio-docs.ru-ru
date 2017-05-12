---
title: "IActiveScriptSite::OnStateChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnStateChange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnStateChange"
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSite::OnStateChange
Уведомляет основное приложение о том, что обработчик скриптов был изменен состояния.  
  
## Синтаксис  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### Параметры  
 `ssScriptState`  
 \[in\] вычисление, указывающее новое состояние сценария.  См. в описании метода [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) описание состояний.  
  
## Возвращаемое значение  
 Возвращает значение `S_OK` в случае успеха.  
  
## См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)