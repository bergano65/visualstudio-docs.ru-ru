---
title: "IDebugReference2::GetParent | Microsoft Docs"
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
  - "IDebugReference2::GetParent"
helpviewer_keywords: 
  - "IDebugReference2::GetParent"
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetParent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает родительскую ссылку справки.  Зарезервировано для использования в будущем.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetParent (   
   IDebugReference2** ppParent  
);  
```  
  
```c#  
int GetParent (   
   out IDebugReference2 ppParent  
);  
```  
  
#### Параметры  
 `ppParent`  
 \[out\] возвращает [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объект, представляющий родительский элемент этого свойства.  
  
## Возвращаемое значение  
 Всегда возвращает значение `E_NOTIMPL`.  
  
## См. также  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)