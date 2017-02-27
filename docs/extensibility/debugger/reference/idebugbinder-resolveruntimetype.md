---
title: "IDebugBinder::ResolveRuntimeType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::ResolveRuntimeType"
helpviewer_keywords: 
  - "Метод IDebugBinder::ResolveRuntimeType"
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод определяет тип объекта во время выполнения.  
  
## Синтаксис  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```c#  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### Параметры  
 `pObject`  
 \[in\] IDebugObject иметь разрешения.  
  
 `ppResolved`  
 \[out\] возвращает тип объекта в IDebugField.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Тип объекта во время выполнения не всегда известен во время компиляции.  Например, использование полиморфизм, аргумент можно передать функции в качестве своего базового класса, например класс кнопки.  Фактический аргумент может быть производным классом, например класс переключателя.  
  
## См. также  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)