---
title: "IDebugProperty2::GetDerivedMostProperty | Microsoft Docs"
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
  - "IDebugProperty2::GetDerivedMostProperty"
helpviewer_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает выведенное\-больше всего свойство свойства.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### Параметры  
 `ppDerivedMost`  
 \[out\] возвращает IDebugProperty2 объект, представляющий выведенное\-больше всего свойство.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `S_GETDERIVEDMOST_NO_DERIVED_MOST` если выведенное\-больше всего свойство, которое требуется получить.  
  
## Заметки  
 Например, если это свойство содержит объект, реализующий `ClassRoot` но в действительности создания экземпляра которого  `ClassDerived` это является производным от  `ClassRoot`затем этот метод возвращает  [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) описание объекта  `ClassDerived` объект.  
  
## См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)