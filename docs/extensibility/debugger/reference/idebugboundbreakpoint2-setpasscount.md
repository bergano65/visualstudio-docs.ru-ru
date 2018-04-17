---
title: IDebugBoundBreakpoint2::SetPassCount | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 589792a9309565496b4d1ab73e1867055bcdf3bc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Задает или изменяет количество прохода, связанные с данная связанная точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bpPassCount`  
 [in] [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структуры, указывающее число проход.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_BP_DELETED` Если состояние объекта связанная точка останова устанавливается `BPS_DELETED` (частью [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисления).  
  
## <a name="remarks"></a>Примечания  
 Число проход определяет срабатывания точки останова. Текущий этап и число попаданий можно получить, вызвав [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) метод.  
  
 Теряется любым количеством pass, который был ранее связан с этой точкой останова.  
  
## <a name="see-also"></a>См. также  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)