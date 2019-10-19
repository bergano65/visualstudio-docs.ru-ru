---
title: 'IDebugApplication110:: Каллаблеваитфорхандлес | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575076"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Ожидает сигнала любого из указанных дескрипторов, чтобы обеспечить передачу межпотоковых вызовов в этот поток. Этот метод должен вызываться из потока отладчика.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) реализуется с помощью PDM v 11.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Параметры  
 `handleCount`  
 Количество дескрипторов, которые нужно ожидать.  
  
 `pHandles`  
 Набор дескрипторов для ожидания.  
  
 `pIndex`  
 Если значение HRESULT равно S_OK, индекс в `pHandles` для дескриптора, который был сигнальным.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)