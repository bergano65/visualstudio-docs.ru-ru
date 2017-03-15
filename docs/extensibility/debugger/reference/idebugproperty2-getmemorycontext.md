---
title: "IDebugProperty2::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugProperty2::GetMemoryContext"
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProperty2::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает контекст памяти значения свойства.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetMemoryContext (   
   IDebugMemoryContext2** ppMemory  
);  
```  
  
```c#  
int GetMemoryContext(  
   out IDebugMemoryContext2 ppMemory  
);  
```  
  
#### Параметры  
 `ppMemory`  
 \[out\] возвращает [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объект, представляющий память, связанный с данным свойством.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT`, если контекст памяти, который необходимо извлечь.  
  
## См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)