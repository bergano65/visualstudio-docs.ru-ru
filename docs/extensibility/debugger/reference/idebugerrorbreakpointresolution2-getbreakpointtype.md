---
title: "IDebugErrorBreakpointResolution2::GetBreakpointType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorBreakpointResolution2::GetBreakpointType"
helpviewer_keywords: 
  - "IDebugErrorBreakpointResolution2::GetBreakpointType"
ms.assetid: 0bdb1152-4752-4464-ae7c-6d666dc293b7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugErrorBreakpointResolution2::GetBreakpointType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает тип точки останова.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```c#  
int GetBreakpointType(   
   out enum_BP_TYPE pBPType  
);  
```  
  
#### Параметры  
 `pBPType`  
 \[out\] возвращает значение [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) перечисление, описывающее тип точки останова.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод возвращает тип точки останова, которую не удалось привязать, таким образом, требующих события точки останова ошибки.  
  
## Пример  
 В следующем примере показано, как реализовать этот метод для простого `CDebugErrorBreakpointResolution` объект, предоставляющий  [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) интерфейс.  
  
```  
HRESULT CDebugErrorBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPERESI_BPRESLOCATION flag is set in BPERESI_FIELDS.    
      if (IsFlagSet(m_bpErrorResolutionInfo.dwFields, BPERESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpErrorResolutionInfo.bpResLocation.bpType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
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
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)