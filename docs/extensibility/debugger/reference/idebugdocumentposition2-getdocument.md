---
title: "IDebugDocumentPosition2::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetDocument"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetDocument"
ms.assetid: eaa172c9-5748-4ce1-a0e2-33c2063f6752
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает содержащий документ.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetDocument(   
   IDebugDocument2** ppDoc  
);  
```  
  
```c#  
int GetDocument(   
   out IDebugDocument2 ppDoc  
);  
```  
  
#### Параметры  
 `ppDoc`  
 \[out\] возвращает [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) объект, представляющий документ, содержащей эту позицию.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)