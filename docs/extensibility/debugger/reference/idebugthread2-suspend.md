---
title: IDebugThread2::Suspend | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b3037a91c838def73b559938128dba831ffe30ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902179"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Приостанавливает поток.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwSuspendCount`  
 [out] Возвращает счетчик приостановок после операцию приостановки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Каждый вызов этого метода увеличивает счетчик приостановок выше 0. Этот счетчик приостановок отображается в **потоков** окно отладки.  
  
 Для каждого вызова этого метода, должно существовать последующему вызову [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)