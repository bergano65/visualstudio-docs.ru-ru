---
title: "IDebugFunctionObject2::CreateStringObjectWithLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreateStringObjectWithLength"
  - "IDebugFunctionObject2::CreateStringObjectWithLength"
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject2::CreateStringObjectWithLength
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает объект типа String, в котором имеет определенной длины.  
  
## Синтаксис  
  
```cpp#  
HRESULT CreateStringObjectWithLength (  
   LPCOLESTR      pcstrString,  
   UINT           uiLength,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateStringObjectWithLength (  
   string           pcstrString,  
   uint             uiLength,  
   out IDebugObject ppObject  
);  
```  
  
#### Параметры  
 `pcstrString`  
 \[in\] строковое значение для строкового объекта.  
  
 `uiLength`  
 \[in\] длина строки \(в байтах\).  
  
 `ppObject`  
 \[out\] возвращает IDebugObject объект, представляющий только что созданный строковый объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)