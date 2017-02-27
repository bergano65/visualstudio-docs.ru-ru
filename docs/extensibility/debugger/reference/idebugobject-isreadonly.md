---
title: "IDebugObject::IsReadOnly | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::IsReadOnly"
helpviewer_keywords: 
  - "Метод IDebugObject::IsReadOnly"
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::IsReadOnly
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет, является ли данный объект только для чтения.  
  
## Синтаксис  
  
```cpp#  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```c#  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### Параметры  
 `pfIsReadOnly`  
 \[out\] возвращает ненулевое \(`TRUE`если этот объект доступен только для чтения. в противном случае, возвращает нуль \(`FALSE`\).  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Доступный только для чтения объект не может иметь свое измененное значение, после того как он был создан.  
  
## См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)