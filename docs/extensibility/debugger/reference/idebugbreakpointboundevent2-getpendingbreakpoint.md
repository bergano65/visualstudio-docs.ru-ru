---
title: IDebugBreakpointBoundEvent2::GetPendingBreakpoint | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
ms.assetid: 6da7ed86-b412-4964-b6a3-0687a66f63fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b37f36942ab5797af980fdf98b50fa71fbda4e59
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938910"
---
# <a name="idebugbreakpointboundevent2getpendingbreakpoint"></a>IDebugBreakpointBoundEvent2::GetPendingBreakpoint
Получает ожидающая точка останова, к которому осуществляется привязка.  
  
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
 [out] Возвращает [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , представляющий привязываемого ожидающая точка останова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CBreakpointSetDebugEventBase** объекта, который предоставляет [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) интерфейс.  
  
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