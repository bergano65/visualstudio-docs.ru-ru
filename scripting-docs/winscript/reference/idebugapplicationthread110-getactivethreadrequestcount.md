---
title: 'IDebugApplicationThread110:: Жетактивесреадрекуесткаунт | Документация Майкрософт'
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
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574478"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Возвращает число запросов потока от механизмов переключения потоков PDM, которые в настоящее время обрабатываются. Это число обычно равно 0 или 1. Однако это число может быть выше, если один вызов потока начинает обработку, но запускает синхронный вызов из потока или, в противном случае, приостанавливает поток и разрешает повторно обрабатывать входящие вызовы (например, запуская [IRemoteDebugApplicationEvents Событие интерфейса](../../winscript/reference/iremotedebugapplicationevents-interface.md) , которое выдается в потоке отладчика.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) реализуется с помощью PDM v 11.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Параметры  
 `puiThreadRequests`  
 заполняет Число запросов потока.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)