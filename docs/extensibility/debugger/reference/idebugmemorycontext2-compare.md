---
title: "IDebugMemoryContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Compare"
helpviewer_keywords: 
  - "Метод IDebugMemoryContext2::Compare"
  - "Compare - метод"
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Сравнивает контекст памяти на каждый контекст в заданном массиве способом, отображаемом которым следует сравнить флаги, возвращая индекс первого контекста, соответствующего.  
  
## Синтаксис  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```c#  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### Параметры  
 `compare`  
 \[in\] значение из [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md) перечисление, которое указывает тип сравнения.  
  
 `rgpMemoryContextSet`  
 \[in\] массив ссылок на [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объекты для сравнения с.  
  
 `dwMemoryContextSetLen`  
 \[in\] число контекстов в `rgpMemoryContextSet` массив.  
  
 `pdwMemoryContext`  
 \[out\] возвращает индекс первого контекста памяти, который выполняет сравнение.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_COMPARE_CANNOT_COMPARE` если 2 контекста нельзя сравнивать.  
  
## Заметки  
 Отладчик \(DE\) не должен поддерживать все типы сравнений, но он должен поддерживать хотя бы `CONTEXT_EQUAL`"  `CONTEXT_LESS_THAN`"  `CONTEXT_GREATER_THAN` и  `CONTEXT_SAME_SCOPE`.  
  
## См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)