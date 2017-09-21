---
title: "IDebugReference2::GetMemoryBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetMemoryBytes"
helpviewer_keywords: 
  - "IDebugReference2::GetMemoryBytes"
ms.assetid: 2006cb2b-1dfa-4a2d-8e3e-db2ce0302e0d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает объем памяти, которые физически содержат значения ссылки.  Зарезервировано для использования в будущем.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```c#  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### Параметры  
 `ppMemoryBytes`  
 \[out\] возвращает [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) объект, который может использоваться для получения память, содержащую значения ссылки.  
  
## Возвращаемое значение  
 Всегда возвращает значение `E_NOTIMPL`.  
  
## См. также  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)