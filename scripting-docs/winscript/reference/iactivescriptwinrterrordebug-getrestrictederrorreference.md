---
title: "IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference"
ms.assetid: fcf60971-9518-4b24-a3a6-1e2e30a02cea
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
Возвращает ошибку ссылки Windows ограничиванную средой выполнения, если оно известно.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug — интерфейс](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT GetRestrictedErrorReference([out] BSTR * referenceString);  
```  
  
#### Параметры  
 `referenceString`  
 \[out\] строка ошибки ссылок.  
  
## См. также  
 [IActiveScriptWinRTErrorDebug — интерфейс](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)