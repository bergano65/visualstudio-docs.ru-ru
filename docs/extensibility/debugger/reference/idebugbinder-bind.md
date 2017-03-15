---
title: "IDebugBinder::Bind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::Bind"
helpviewer_keywords: 
  - "Метод IDebugBinder::Bind"
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::Bind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод получает контекст или объекта памяти, содержащий текущее значение символа.  
  
## Синтаксис  
  
```cpp#  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### Параметры  
 `pContainer`  
 \[in\] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) он содержит дочерний элемент, на который ссылается by  `pField`.  
  
 `pField`  
 \[in\] IDebugField представляет символ.  
  
 `ppObject`  
 \[out\] возвращает `IDebugObject` представляет экземпляр символа.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)