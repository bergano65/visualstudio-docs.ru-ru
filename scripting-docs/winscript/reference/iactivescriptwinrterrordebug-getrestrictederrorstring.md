---
title: "IActiveScriptWinRTErrorDebug::GetRestrictedErrorString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetRestrictedErrorString"
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
Возвращает строку ошибки Windows ограничиванную средой выполнения, если оно известно.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug — интерфейс](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);  
  
```  
  
#### Параметры  
 `errorString`  
 \[out\] \- это строка с ограничениями ошибки.  
  
## См. также  
 [IActiveScriptWinRTErrorDebug — интерфейс](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)