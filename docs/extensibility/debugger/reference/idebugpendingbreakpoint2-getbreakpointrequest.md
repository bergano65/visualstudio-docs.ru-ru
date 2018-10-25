---
title: IDebugPendingBreakpoint2::GetBreakpointRequest | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest
helpviewer_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest method
- GetBreakpointRequest method
ms.assetid: cb1e36aa-4302-455c-98fb-6638a1ef5c46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db1553295e3b8827330c78c1f6f35c21f1380cb4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921006"
---
# <a name="idebugpendingbreakpoint2getbreakpointrequest"></a>IDebugPendingBreakpoint2::GetBreakpointRequest
Возвращает точки останова запрос, который был использован для создания этого ожидающая точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetBreakpointRequest(   
   IDebugBreakpointRequest2** ppBPRequest  
);  
```  
  
```csharp  
int GetBreakpointRequest(   
   out IDebugBreakpointRequest2 ppBPRequest  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppBPRequest`  
 [out] Возвращает [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) объект, представляющий запроса точки останова, которая использовалась для создания данного ожидающих точек останова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` Если точка останова была удалена.  
  
## <a name="see-also"></a>См. также  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)