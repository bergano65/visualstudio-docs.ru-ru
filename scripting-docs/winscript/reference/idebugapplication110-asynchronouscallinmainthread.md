---
title: IDebugApplication110::AsynchronousCallInMainThread | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 236a6585d5d5844f282d8ecf5820ac8fdfb49648
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725744"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Выполняет асинхронный вызов в основном потоке.  
  
> [!IMPORTANT]
>  [Idebugapplication110 — интерфейс](../../winscript/reference/idebugapplication110-interface.md) — реализованный PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pptc`  
 [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) для вызова.  
  
 `dwParam1`  
 Первый параметр вызова.  
  
 `dwParam1`  
 Первый параметр вызова.  
  
 `dwParam2`  
 Второй параметр вызова.  
  
 `dwParam3`  
 Третий параметр вызова.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)