---
title: "IDebugExceptionEvent2::GetExceptionDescription | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::GetExceptionDescription"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::GetExceptionDescription"
ms.assetid: d07d458f-5729-47e4-9b77-1bd59c61a75a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExceptionEvent2::GetExceptionDescription
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает displayable описание исключения.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetExceptionDescription(   
   BSTR* pbstrDescription  
);  
```  
  
```c#  
int GetExceptionDescription(   
   out string pbstrDescription  
);  
```  
  
#### Параметры  
 `pbstrDescription`  
 \[out\] возвращает displayable описание исключения.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Строка, возвращаемая этим методом, обычно имя исключения и отображается в **Вывод** окно при возникновении исключения.  
  
## См. также  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)