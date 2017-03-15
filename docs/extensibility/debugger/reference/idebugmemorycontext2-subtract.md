---
title: "IDebugMemoryContext2::Subtract | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Subtract"
helpviewer_keywords: 
  - "Вычитание метод"
  - "Метод IDebugMemoryContext2::Subtract"
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вычитает указанное значение из текущего контекста и возвращает новый контекст.  
  
## Синтаксис  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Параметры  
 `dwCount`  
 \[in\] число байтов в затуханию памяти.  
  
 `ppMemCxt`  
 \[out\] возвращает новую [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Контекст памяти адрес, поэтому вычитания значения из адреса создает новый адрес, который требует создания нового интерфейса контекста.  
  
 Этот метод должен всегда создания нового контекста, даже если полученный адрес вне области памяти, связанной с данным контекстом.  Единственное исключение из этого, если объем памяти, выделяемой для нового контекста или если `ppMemCxt` значение NULL \(ошибка\).  
  
## См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)