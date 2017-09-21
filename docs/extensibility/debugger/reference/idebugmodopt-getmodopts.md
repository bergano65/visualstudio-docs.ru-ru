---
title: "IDebugModOpt::GetModOpts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugModOpt::GetModOpts"
  - "GetModOpts"
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugModOpt::GetModOpts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает список необязательных modifiers.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```c#  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число возвращаемых элементов.  
  
 `rgelt`  
 \[out\] возвращает массив, содержащий параметры.  
  
 `pceltFetched`  
 \[in, out\] число элементов, возвращенных в `rgelt` массив.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)