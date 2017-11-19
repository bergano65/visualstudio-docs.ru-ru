---
title: "IDebugBoundBreakpoint2::SetHitCount | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9286550d694430e64a410c70abda2333c3322958
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Задает число попаданий для связанная точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetHitCount(   
   DWORD dwHitCount  
);  
```  
  
```csharp  
int SetHitCount(   
   uint dwHitCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwHitCount`  
 [in] Число попаданий для задания.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_BP_DELETED` Если состояние объекта связанная точка останова устанавливается `BPS_DELETED` (частью [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисления).  
  
## <a name="remarks"></a>Примечания  
 Число попаданий — количество раз, когда результат этой точки останова во время выполнения текущего сеанса.  
  
 Этот метод обычно вызывается обработчиком отладки, чтобы обновить текущий счетчик числа попаданий в эту точку останова.  
  
## <a name="see-also"></a>См. также  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)