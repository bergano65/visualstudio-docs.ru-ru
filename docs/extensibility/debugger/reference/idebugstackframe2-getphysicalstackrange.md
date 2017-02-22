---
title: "IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs"
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
  - "IDebugStackFrame2::GetPhysicalStackRange"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает представление компьютер\-зависимой ячейки диапазона физических адресов, связанных с кадром стека.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```c#  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### Параметры  
 `paddrMin`  
 \[out\] возвращает наименьший физический адрес, связанный с данным кадром стека.  
  
 `paddrMax`  
 \[out\] возвращает наибольший физический адрес, связанный с данным кадром стека.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Информация, возвращаемая этим методом, используется сеансом \(SDM\) диспетчер отладки для сортировки кадры стека.  
  
 Ожидается стек вызовов вниз увеличивается, то есть новые кадры стека добавляются на все больше нижнего адреса памяти.  Архитектура среды выполнения должна обеспечивать физические диапазона стека, которые соответствуют данному допущению.  
  
## См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)