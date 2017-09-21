---
title: "IDebugBreakpointResolution2::GetBreakpointType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointResolution2::GetBreakpointType"
helpviewer_keywords: 
  - "IDebugBreakpointResolution2::GetBreakpointType"
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBreakpointResolution2::GetBreakpointType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает тип точки останова, представленной этим разрешением.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```c#  
int GetBreakpointType(   
   out enum_ BP_TYPE pBPType  
);  
```  
  
#### Параметры  
 `pBPType`  
 \[out\] возвращает значение [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) перечисление, определяющее тип этой точки останова.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает E\_FAIL, если `bpResLocation` поле, связанное  [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структура является недопустимой.  
  
## Заметки  
 Точка останова может быть кодом или точками останова в данных, например.  
  
## Пример  
 В следующем примере показано, как реализовать этот метод для простого `CDebugBreakpointResolution` объект, предоставляющий  [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) интерфейс.  
  
```  
HRESULT CDebugBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPRESI_BPRESLOCATION flag is set in BPRESI_FIELDS.    
      if (IsFlagSet(m_bpResolutionInfo.dwFields, BPRESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpResolutionInfo.bpResLocation.bpType;    
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
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BPRESI\_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)