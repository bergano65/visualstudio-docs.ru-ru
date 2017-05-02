---
title: "IActiveScriptParse::InitNew | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.InitNew
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_InitNew"
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::InitNew
Инициализирует обработчика скриптов.  
  
## Синтаксис  
  
```  
HRESULT InitNew(void);  
```  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или `E_FAIL`, если ошибка произошла во время инициализации.  
  
## Заметки  
 Прежде чем обработчик скриптов можно использовать один из следующих методов следует вызвать: `IPersist*::Load`, `IPersist*::InitNew` или `IActiveScriptParse::InitNew`.  Семантика этого метода идентична `IPersistStreamInit::InitNew`, в котором этот метод сообщает, что обработчик скриптов инициализируется.  Обратите внимание, что она недопустима для вызова и `IPersist*::InitNew` или `IActiveScriptParse::InitNew` и `IPersist*::Load`, она также не является допустимой вызвать `IPersist*::InitNew`, `IActiveScriptParse::InitNew` или `IPersist*::Load` несколько раз.  
  
## См. также  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)