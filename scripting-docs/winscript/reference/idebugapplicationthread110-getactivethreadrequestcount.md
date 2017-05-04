---
title: "IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::GetActiveThreadRequestCount"
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugApplicationThread110::GetActiveThreadRequestCount
Возвращает количество запросов потока из механизмов передачи потока PDM, которые в настоящее время обрабатываются.  Это значение обычно равно 0 или 1.  Однако это число может быть более высоком уровне при запуске одного вызова поток, обрабатывающий но активируют синхронный вызов из потока, в противном случае приостанавливает поток и позволяет входящие вызовы, которые необходимо обработать повторно, то \(например, с помощью [Интерфейс IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md) активировать событие, которое выдается в потоке отладчика\).  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 — интерфейс](../../winscript/reference/idebugapplicationthread110-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
  
```  
  
#### Параметры  
 `puiThreadRequests`  
 \[out\] количество потоков в пул.  
  
## См. также  
 [IDebugApplicationThread110 — интерфейс](../../winscript/reference/idebugapplicationthread110-interface.md)