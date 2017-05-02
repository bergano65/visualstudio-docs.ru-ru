---
title: "IActiveScriptWinRTErrorDebug::GetCapabilitySid | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetCapabilitySid"
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetCapabilitySid
Возвращает идентификатор безопасности возможности для ошибок среды выполнения Windows, если оно известно.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug — интерфейс](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### Параметры  
 `capabilitySid`  
 Идентификатор безопасности возможности ошибки.  
  
## См. также  
 [IActiveScriptWinRTErrorDebug — интерфейс](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)