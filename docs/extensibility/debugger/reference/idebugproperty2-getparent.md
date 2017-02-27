---
title: "IDebugProperty2::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetParent"
helpviewer_keywords: 
  - "IDebugProperty2::GetParent"
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetParent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает родительское свойство свойства.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetParent (   
   IDebugProperty2** ppParent  
);  
```  
  
```c#  
int GetParent (   
   out IDebugProperty2 ppParent  
);  
```  
  
#### Параметры  
 `ppParent`  
 \[out\] возвращает IDebugProperty2 объект, представляющий родительский элемент свойства.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `S_GETPARENT_NO_PARENT` если родительский объект.  
  
## См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)