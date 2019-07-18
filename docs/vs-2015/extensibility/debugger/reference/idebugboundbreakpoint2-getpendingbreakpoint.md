---
title: IDebugBoundBreakpoint2::GetPendingBreakpoint | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint method
- GetPendingBreakpoint method
ms.assetid: 22f94f81-f8d9-46de-96e9-fae6f3c24903
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2030de26c384405bafaa22582145130a6a2e5da6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156231"
---
# <a name="idebugboundbreakpoint2getpendingbreakpoint"></a>IDebugBoundBreakpoint2::GetPendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает ожидающая точка останова, из которого был создан указанного связанная точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPendingBreakpoint(   
   IDebugPendingBreakpoint2** ppPendingBreakpoint  
);  
```  
  
```csharp  
int GetPendingBreakpoint(   
   out IDebugPendingBreakpoint2 ppPendingBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppPendingBreakpoint`  
 [out] Возвращает [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , представляющий ожидающая точка останова, которая использовалась для создания данного привязан точки останова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Ожидающая точка останова может рассматриваться как коллекция все необходимые сведения, необходимые для привязки точку останова для кода, которые могут применяться для одного или нескольких программ.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простого `CBoundBreakpoint` объекта, который предоставляет [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) интерфейс.  
  
```  
HRESULT CBoundBreakpoint::GetPendingBreakpoint(  
    IDebugPendingBreakpoint2** ppPendingBreakpoint)  
{    
   HRESULT hr;    
  
   // Check for valid IDebugPendingBreakpoint2 interface pointer.    
   if (ppPendingBreakpoint)    
   {    
      // Be sure that the bound breakpoint has not been deleted. If  
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state != BPS_DELETED)    
      {    
         // Query for the IDebugPendingBreakpoint2 interface.    
         hr = m_pPendingBP->QueryInterface(IID_IDebugPendingBreakpoint2,  
                                           (void**)ppPendingBreakpoint);    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>См. также  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
