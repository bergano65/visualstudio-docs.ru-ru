---
title: "IDebugBoundBreakpoint2::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetState"
helpviewer_keywords: 
  - "Метод GetState"
  - "Метод IDebugBoundBreakpoint2::GetState"
ms.assetid: a40a8382-295e-4916-aae6-ffe3a9cd3f2d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBoundBreakpoint2::GetState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает состояние данного прыгните точка останова.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetState(   
   BP_STATE* pState  
);  
```  
  
```c#  
int GetState(   
   out enum_BP_STATE pState  
);  
```  
  
#### Параметры  
 `pState`  
 \[out\] возвращает значение [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисление, описывающее состояние точек останова.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Пример  
 В следующем примере показано, как реализовать этот метод для простого `CBoundBreakpoint` объект, предоставляющий  [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) интерфейс.  
  
```  
HRESULT CBoundBreakpoint::GetState(BP_STATE* pState)    
{    
   HRESULT hr;    
  
   // Check for a valid pointer to pState and assign the local state variable.    
   if (pState)    
   {    
      *pState = m_state;    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## См. также  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)