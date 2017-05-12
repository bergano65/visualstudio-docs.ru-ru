---
title: "IRemoteDebugApplication110::SetDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::SetDebuggerOptions"
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::SetDebuggerOptions
Вызываемый для обновления параметров отладчика.  Этот метод следует вызывать после [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md).  Метод [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) автоматически сбросить к параметрам по умолчанию.  Параметры имеют значение по умолчанию равно 0 \(SDO\_NONE\).  
  
> [!IMPORTANT]
>  [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT SetDebuggerOptions(  
        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,  
        [in] enum SCRIPT_DEBUGGER_OPTIONS value  
    );  
  
```  
  
#### Параметры  
 `mask`  
 Маска [SCRIPT\_DEBUGGER\_OPTIONS — перечисление](../../winscript/reference/script-debugger-options-enumeration.md).  
  
 `value`  
 Значение типа [SCRIPT\_DEBUGGER\_OPTIONS — перечисление](../../winscript/reference/script-debugger-options-enumeration.md).  
  
## См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 — интерфейс](../../winscript/reference/iremotedebugapplication110-interface.md)