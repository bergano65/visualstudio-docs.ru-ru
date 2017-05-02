---
title: "IDebugApplicationThread110::IsThreadCallable | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsThreadCallable"
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsThreadCallable
Определяет, является ли данный поток находится в состоянии, которое будет обрабатываться, вызываемые с помощью механизмов передачи потока PDM, как SynchronousCallInThread.  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 — интерфейс](../../winscript/reference/idebugapplicationthread110-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### Параметры  
 `pfIsCallable`  
 \[out\] `true`, если поток, доступный для вызова; в противном случае `false`.  
  
## См. также  
 [IDebugApplicationThread110 — интерфейс](../../winscript/reference/idebugapplicationthread110-interface.md)