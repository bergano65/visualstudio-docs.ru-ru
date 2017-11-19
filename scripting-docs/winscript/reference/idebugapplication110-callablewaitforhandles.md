---
title: "IDebugApplication110::CallableWaitForHandles | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b259f5296f8e0b32def793a81e4c2e1069643306
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Ожиданий для любого указанного дескрипторов в целях сигнализировать, обеспечив при этом межпоточные вызовы должны быть учтены данного потока. Этот метод должен вызываться из потока отладчика.  
  
> [!IMPORTANT]
>  [Idebugapplication110 — интерфейс](../../winscript/reference/idebugapplication110-interface.md) — реализованный PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Параметры  
 `handleCount`  
 Число дескрипторов ожидания.  
  
 `pHandles`  
 Набор дескрипторов ожидания.  
  
 `pIndex`  
 Если значение HRESULT равно S_OK, индекс в `pHandles` для дескриптора, которое было указано.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)