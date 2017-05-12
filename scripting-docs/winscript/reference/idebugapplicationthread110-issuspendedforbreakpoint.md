---
title: "IDebugApplicationThread110::IsSuspendedForBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsSuspendedForBreakPoint"
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsSuspendedForBreakPoint
Указывает, было ли Позвонитьо [IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) в этом потоке и еще не завершена.  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 — интерфейс](../../winscript/reference/idebugapplicationthread110-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### Параметры  
 `pfIsSuspended`  
 \[out\] `true` если поток приостанавливается для точки останова, в противном случае `false`.  
  
## См. также  
 [IDebugApplicationThread110 — интерфейс](../../winscript/reference/idebugapplicationthread110-interface.md)