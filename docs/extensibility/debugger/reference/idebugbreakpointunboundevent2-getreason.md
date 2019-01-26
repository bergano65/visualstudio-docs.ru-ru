---
title: IDebugBreakpointUnboundEvent2::GetReason | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2dc730be1ac49bddb8406a5f3322e800c86dce50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041872"
---
# <a name="idebugbreakpointunboundevent2getreason"></a>IDebugBreakpointUnboundEvent2::GetReason
Получает причину, по которой был отсоединен точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetReason(   
   BP_UNBOUND_REASON* pdwUnboundReason  
);  
```  
  
```csharp  
int GetReason(   
   out enum_ BP_UNBOUND_REASON pdwUnboundReason  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwUnboundReason`  
 [out] Возвращает значение из [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) перечисление, определяющее, причина, точка останова был отсоединен.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Причины: точку останова, лежащему в другое расположение, после определения, что точка останова была привязана в ошибки или изменить и продолжить операции.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CBreakpointUnboundDebugEventBase** объекта, который предоставляет [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) интерфейс.  
  
```cpp  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(  
    BP_UNBOUND_REASON* pdwUnboundReason)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( EVAL(pdwUnboundReason) )  
    {  
        *pdwUnboundReason = m_dwReason;  
  
        hRes = S_OK;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)