---
title: "IDebugField::GetType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetType"
helpviewer_keywords: 
  - "Метод IDebugField::GetType"
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает тип поля.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```c#  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### Параметры  
 `ppType`  
 \[out\] возвращает тип поля как другие IDebugField объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)