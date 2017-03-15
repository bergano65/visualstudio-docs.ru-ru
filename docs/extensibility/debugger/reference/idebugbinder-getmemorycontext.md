---
title: "IDebugBinder::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::GetMemoryContext"
helpviewer_keywords: 
  - "Метод IDebugBinder::GetMemoryContext"
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод преобразует или расположение объекта или адрес памяти к контексту памяти.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Параметры  
 `pField`  
 \[in\] IDebugField описание объект для поиска.  If `NULL`после этого используйте  `dwConstant` вместо этого.  
  
 `dwConstant`  
 \[in\] адрес памяти постоянным, а как 0x5000.  
  
 `ppMemCxt`  
 \[out\] возвращает [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс, представляющий адрес объекта или адрес в памяти.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)