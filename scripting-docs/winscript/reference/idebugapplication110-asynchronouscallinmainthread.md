---
title: IDebugApplication110::AsynchronousCallInMainThread | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 2fc497e6621b309eed8fbb7e7c4e79f1ebb24c9c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146621"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Делает асинхронный вызов в основном потоке.  
  
> [!IMPORTANT]
>  [Интерфейс IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) является реализуется PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pptc`  
 [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) объект для вызова.  
  
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