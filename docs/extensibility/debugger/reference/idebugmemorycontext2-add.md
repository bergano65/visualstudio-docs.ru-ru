---
title: "IDebugMemoryContext2::Add | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Add"
helpviewer_keywords: 
  - "Метод IDebugMemoryContext2::Add"
  - "Add - метод"
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Add
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Добавляет указанное значение к текущему контексту и возвращает новый контекст.  
  
## Синтаксис  
  
```cpp#  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Параметры  
 `dwCount`  
 \[in\] значение, добавляемое к текущему контексту.  
  
 `ppMemCxt`  
 \[out\] возвращает новую [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Контекст памяти адрес, поэтому добавление значение адреса создает новый адрес, который требует создания нового интерфейса контекста.  
  
 Этот метод должен всегда создания нового контекста, даже если полученный адрес вне области памяти, связанной с данным контекстом.  Единственное исключение из этого, если объем памяти, выделяемой для нового контекста или если `ppMemCxt` значение NULL \(ошибка\).  
  
## См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)