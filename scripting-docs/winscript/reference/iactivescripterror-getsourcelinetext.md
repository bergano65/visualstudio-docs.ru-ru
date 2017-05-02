---
title: "IActiveScriptError::GetSourceLineText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourceLineText"
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourceLineText
Извлекает линию в исходном файле, где произошла ошибка, пока обработчик скриптов выполняется скрипт.  
  
## Синтаксис  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## Параметр  
 `pbstrSourceLine`  
 \[out\] адрес буфера, который получает линию исходного кода, в которой произошла ошибка.  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или `E_FAIL`, если не была восстановитьа линию в файле источника.  
  
## См. также  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)