---
title: 'IDebugApplicationNode100:: Сетфилтерфоревентсинк | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f85241bee7b35d40bf193a613a6fefda4265be6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574726"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Задает фильтр для определенной реализации [интерфейса идебугаппликатионнодивентс](../../winscript/reference/idebugapplicationnodeevents-interface.md) . Он позволяет отладчикам скриптов отфильтровать созданные компилятором дочерние узлы приложения, чтобы PDM больше не отправлял события при их создании или удалении. По умолчанию будут отправлены все узлы.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) реализуется с помощью PDM v 10.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwCookie`  
 Файл cookie фильтра.  
  
 `filter`  
 Фильтр.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)