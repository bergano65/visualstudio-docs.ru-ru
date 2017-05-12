---
title: "IActiveScript::GetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptState"
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptState
Получает текущее состояние обработчика скриптов.  Этот метод может быть вызван из потоков, не относящихся к базовому без привести к появлению выноски отличные от причины для размещения объектов или к интерфейсу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## Синтаксис  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### Параметры  
 `pss`  
 \[out\] адрес переменной, которая возвращает значение, определенные в перечислении [Перечисление SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md).  Значение показывает текущее состояние обработчика скриптов, связанного с вызывающим потоком.  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или `E_POINTER`, если указан недопустимый указатель.  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)