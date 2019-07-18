---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3df2f0c44e42cf9e2c2aa846db4b88821fd73996
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440571"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Возвращает число потоков запросов из потока PDM переключение механизмы, которые сейчас обрабатываются. Это число обычно 0 или 1. Тем не менее, число может быть выше, если один вызов поток начинает обработку, но вызывает синхронный вызов из потока, или в противном случае приостанавливает поток и разрешает входящие вызовы для повторной обработки (например, отключая [ Интерфейс IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md) событие, которое выдается в потоке отладчика).  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) является реализуется PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Параметры  
 `puiThreadRequests`  
 [out] Число потоков запросов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)