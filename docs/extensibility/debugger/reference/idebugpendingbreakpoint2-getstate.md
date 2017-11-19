---
title: "IDebugPendingBreakpoint2::GetState | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPendingBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugPendingBreakpoint2::GetState method
ms.assetid: e88d543f-2e83-4ba7-86ca-f874e39955ff
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13a99c05d76ac986d45664397e9c4d205df22bb0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpendingbreakpoint2getstate"></a>IDebugPendingBreakpoint2::GetState
Получает состояние ожидающая точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetState(   
   PENDING_BP_STATE_INFO* pState  
);  
```  
  
```csharp  
int GetState(   
   PENDING_BP_STATE_INFO[] pState  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pState`  
 [in, out] Объект [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) структуру, которая содержит описание этого аспекта ожидающих точек останова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)