---
title: "IActiveScriptError::GetExceptionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetExceptionInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetExceptionInfo"
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetExceptionInfo
Извлекает сведения об ошибке, которая произошла во время выполнения скрипт обработчика сценариев.  
  
## Синтаксис  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### Параметры  
 `pexcepinfo`  
 \[out\] адрес структуры `EXCEPINFO`, которая получает сведения об ошибке.  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или `E_FAIL`, если произошла ошибка.  
  
## См. также  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)