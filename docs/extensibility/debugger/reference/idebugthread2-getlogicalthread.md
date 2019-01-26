---
title: IDebugThread2::GetLogicalThread | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0034daecab2543d9a48a627a26a88ee84a872f73
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945935"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Отладчики не реализуют этот метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStackFrame`  
 [in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , представляющий кадр стека.  
  
 `ppLogicalThread`  
 [out] Возвращает `IDebugLogicalThread2` интерфейс, который представляет логический поток. Реализация ядра отладки следует выбрать значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Отладка ядра реализации всегда возвращают `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)