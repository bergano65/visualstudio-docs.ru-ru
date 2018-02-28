---
title: "IDebugApplicationThread110::GetActiveThreadRequestCount | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb4d19bb77a4380c3c0a04f7e7808b82ca3f6ae4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Возвращает число потоков запросов из потока PDM переключение механизмы, обрабатываемых в данный момент. Это число обычно 0 или 1. Тем не менее, число может быть выше, если один вызов поток начинает обработку, но активирует синхронный вызов из потока, или в противном случае приостанавливает работу потока и позволяет повторной обработки входящих вызовов (например, путем активации [ Интерфейс IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md) событие, которое выдается в потоке отладчика).  
  
> [!IMPORTANT]
>  [Idebugapplicationthread110 — интерфейс](../../winscript/reference/idebugapplicationthread110-interface.md) — реализованный PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Параметры  
 `puiThreadRequests`  
 [out] Число потоков запросов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)