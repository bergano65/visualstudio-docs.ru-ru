---
title: "IDebugPendingBreakpoint2::EnumBoundBreakpoints | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::EnumBoundBreakpoints"
helpviewer_keywords: 
  - "Метод EnumBoundBreakpoints"
  - "Метод IDebugPendingBreakpoint2::EnumBoundBreakpoints"
ms.assetid: 179c7c54-8446-462d-b099-e0f9cf06dc52
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::EnumBoundBreakpoints
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Перечисляет все точки останова из ожидающих привязанные этой точки останова.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumBoundBreakpoints(   
   IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```c#  
int EnumBoundBreakpoints(   
   out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### Параметры  
 `ppEnum`  
 \[out\] возвращает IEnumDebugBoundBreakpoints2 объект, перечисляющий связанные точки останова.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_BP_DELETED` если точка останова удалена.  
  
## Пример  
 В следующем примере показано, как реализовать этот метод для простого `CPendingBreakpoint` объект, предоставляющий  [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейс.  
  
```cpp#  
HRESULT CPendingBreakpoint::EnumBoundBreakpoints(IEnumDebugBoundBreakpoints2** ppEnum)    
{    
   HRESULT hr;    
  
   // Verify that the passed IEnumDebugBoundBreakpoints2 interface pointer   
   // is valid.    
   if (ppEnum)    
   {    
      *ppEnum = NULL;  
  
      // Verify that the pending breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state.state != PBPS_DELETED)    
      {    
         // If the bound breakpoint member variable is valid.  
         if (m_pBoundBP)    
         {    
            // Get the bound breakpoint.    
            CComPtr<IDebugBoundBreakpoint2> spBoundBP;    
            hr = m_pBoundBP->QueryInterface(&spBoundBP);    
            assert(hr == S_OK);    
            if (hr == S_OK)    
            {    
               // Create the bound breakpoint enumerator.    
               CComObject<CEnumDebugBoundBreakpoints>* pBoundEnum;    
               hr = CComObject<CEnumDebugBoundBreakpoints>::CreateInstance(&pBoundEnum);    
               assert(hr == S_OK);    
               if (hr == S_OK)    
               {    
                  // Initialize the enumerator of bound breakpoints with   
                  // the IDebugBoundBreakpoint2 information.      
                  IDebugBoundBreakpoint2* rgBoundBP[] = { spBoundBP.p };    
                  hr = pBoundEnum->Init(rgBoundBP, &(rgBoundBP[1]), NULL, AtlFlagCopy);    
                  if (hr == S_OK)    
                  {    
                     // Verify that the passed IEnumDebugBoundBreakpoints2     
                     // interface can be queried by the created  
                     // CEnumDebugBoundBreakpoints object.    
                     hr = pBoundEnum->QueryInterface(ppEnum);    
                     assert(hr == S_OK);    
                  }    
  
                  // Otherwise, delete the CEnumDebugBoundBreakpoints object.    
                  if (FAILED(hr))    
                  {    
                     delete pBoundEnum;    
                  }    
               }    
            }    
         }    
         else    
         {    
            hr = S_FALSE;    
         }    
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
  
## См. также  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)