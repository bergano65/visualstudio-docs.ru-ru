---
title: "IDebugApplicationNode100::SetFilterForEventSink | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6db8ea26787427844a92417bf525dba271063cba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Задает фильтр на определенном [интерфейс IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) реализации. Она позволяет отладчики сценариев для фильтрации компилятором дочерних узлов приложения, чтобы PDM больше не будет отправлять события при их создании или удалены. По умолчанию будут отправляться все узлы.  
  
> [!IMPORTANT]
>  [Idebugapplicationnode100 — интерфейс](../../winscript/reference/idebugapplicationnode100-interface.md) — реализованный PDM v10.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
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