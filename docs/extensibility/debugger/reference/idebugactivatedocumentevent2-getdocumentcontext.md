---
title: "IDebugActivateDocumentEvent2::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugActivateDocumentEvent2::GetDocumentContext"
helpviewer_keywords: 
  - "Метод GetDocumentContext"
  - "Метод IDebugActivateDocumentEvent2::GetDocumentContext"
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugActivateDocumentEvent2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает контекст рисования, описывающий позиции в документе, должна быть активным пакетом отладки.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### Параметры  
 `ppDocContext`  
 \[out\] возвращает IDebugDocumentContext2 объект, представляющий позицию в документе исходного файла.  
  
## Заметки  
 Эта позиция может использоваться для указания курсора, например.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)