---
title: "IDebugArrayObject::GetElements | Microsoft Docs"
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
  - "IDebugArrayObject::GetElements"
helpviewer_keywords: 
  - "Метод IDebugArrayObject::GetElements"
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает перечислитель для всех элементов массива.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```c#  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### Параметры  
 `ppEnum`  
 \[out\] возвращает [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) объект, который обеспечивает перечисление по всем элементам.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 В качестве альтернативы используйте [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) и  [GetElement](../Topic/IDebugArrayObject::GetElement.md) методы для перебора элементов.  
  
## См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)