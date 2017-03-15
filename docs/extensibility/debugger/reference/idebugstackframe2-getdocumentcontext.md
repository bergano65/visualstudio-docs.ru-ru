---
title: "IDebugStackFrame2::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetDocumentContext"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetDocumentContext"
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает контекст рисования для этого кадра стека.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppCxt  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppCxt  
);  
```  
  
#### Параметры  
 `ppCxt`  
 \[out\] возвращает IDebugDocumentContext2 объект, представляющий текущую позицию в исходном документе.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод быстрее, чем вызов [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) метод и затем вызывать  [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) метод в контексте кода.  Однако не гарантируется, что каждый обработчик отладки \(DE\) будет реализовывать данный метод.  
  
## См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)   
 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)