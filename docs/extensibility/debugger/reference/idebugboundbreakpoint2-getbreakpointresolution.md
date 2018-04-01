---
title: IDebugBoundBreakpoint2::GetBreakpointResolution | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 19f668c9e71a5c5b31870b1a0d23a76a41b2d6b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Возвращает разрешение точки останова, описывающий эту точку останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetBreakpointResolution(   
   IDebugBreakpointResolution2** ppBPResolution  
);  
```  
  
```csharp  
int GetBreakpointResolution(   
   out IDebugBreakpointResolution2 ppBPResolution  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppBPResolution`  
 [out] Возвращает [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) интерфейс, который представляет одно из следующих действий:  
  
-   Объект разрешения точки останова, описывающий расположение в коде, где были связаны точку останова кода.  
  
-   Расположение данных, где выполнило привязку точки останова по данным.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_BP_DELETED` Если состояние объекта связанная точка останова устанавливается `BPS_DELETED` (частью [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисления).  
  
## <a name="remarks"></a>Примечания  
 Вызовите [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) метод, чтобы определить, является ли точка останова разрешения для кода или данных.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простой `CBoundBreakpoint` объекта, который предоставляет [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) интерфейса.  
  
```  
HRESULT CBoundBreakpoint::GetBreakpointResolution(  
    IDebugBreakpointResolution2** ppBPResolution)  
{    
   HRESULT hr;    
  
   if (ppBPResolution)    
   {    
      // Verify that the bound breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state != BPS_DELETED)    
      {    
         // Query for the IDebugBreakpointResolution2 interface.    
         hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,  
                                       (void **)ppBPResolution);  
         assert(hr == S_OK);    
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
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)