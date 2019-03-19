---
title: IDebugApplication110::CallableWaitForHandles | Документация Майкрософт
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
ms.openlocfilehash: ac5482924288e52895398084aa4f5ab44e151a66
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155374"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Ожиданий для любого из указанных маркеров, который должен получить сигнал при этом межпоточные вызовы публикуемый этим потоком. Этот метод должен вызываться из потока отладчика.  
  
> [!IMPORTANT]
>  [Интерфейс IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) является реализуется PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
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
 Если значение HRESULT равно S_OK, индекс в `pHandles` для дескриптора, который получил сигнал.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)