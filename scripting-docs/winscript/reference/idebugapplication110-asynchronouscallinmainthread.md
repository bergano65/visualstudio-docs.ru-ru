---
title: 'IDebugApplication110:: Асинчронаускаллинмаинсреад | Документация Майкрософт'
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
ms.openlocfilehash: 04c1a2962662d0046c6b9d323a287d580ee0f3e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577394"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Выполняет асинхронный вызов в основном потоке.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) реализуется с помощью PDM v 11.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pptc`  
 Объект [интерфейса идебугсреадкалл](../../winscript/reference/idebugthreadcall-interface.md) для вызова.  
  
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