---
title: IDebugApplicationNode100::SetFilterForEventSink | Документация Майкрософт
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
ms.openlocfilehash: 662c433134bc278f343381edcb4aedf383af6078
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446674"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Задает фильтр для конкретного [интерфейс IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) реализации. Она позволяет отладчиках скриптов отфильтровать компилятором дочерние узлы приложения таким образом, чтобы PDM больше не будет отправлять события при их создании или удалены. По умолчанию будут отправляться все узлы.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) является реализуется PDM v10.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
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