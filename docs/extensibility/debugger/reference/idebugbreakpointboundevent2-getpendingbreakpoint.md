---
title: "IDebugBreakpointBoundEvent2::GetPendingBreakpoint | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointBoundEvent2::GetPendingBreakpoint
helpviewer_keywords: IDebugBreakpointBoundEvent2::GetPendingBreakpoint
ms.assetid: 6da7ed86-b412-4964-b6a3-0687a66f63fe
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b37765534e1cf1791786fb8c31d04f2fa77d0650
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbreakpointboundevent2getpendingbreakpoint"></a>IDebugBreakpointBoundEvent2::GetPendingBreakpoint
Возвращает ожидающая точка останова, к которому осуществляется привязка.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPendingBreakpoint(   
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```cpp  
int GetPendingBreakpoint(   
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppPendingBP`  
 [out] Возвращает [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , представляющий привязываемый ожидающая точка останова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CBreakpointSetDebugEventBase** объекта, который предоставляет [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) интерфейса.  
  
```cpp  
STDMETHODIMP CBreakpointSetDebugEventBase::GetPendingBreakpoint(  
    IDebugPendingBreakpoint2 **ppPendingBP)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppPendingBP )  
    {  
        if ( m_pPendingBP )  
        {  
            *ppPendingBP = m_pPendingBP;  
  
            m_pPendingBP->AddRef();  
  
            hRes = S_OK;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)