---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs"
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
  - "IEEVisualizerDataProvider::SetObjectForVisualizer"
helpviewer_keywords: 
  - "Метод IEEVisualizerDataProvider::SetObjectForVisualizer"
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод изменяет объект, который визуализатор, представляющий.  
  
## Синтаксис  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```c#  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### Параметры  
 `pNewObject`  
 \[in\] объект в набор.  
  
 `error`  
 \[out\] если параметр объекта возникла ошибка, то эта строка содержит сообщение об ошибке.  
  
 `pException`  
 \[out\] если возникла ошибка, то этот объект содержит сведения об исключении.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Он принимает разработчик, чтобы задать сведения об ошибке.  Однако возможно, что некоторые объекты, вызывающие могут только просматривать, что увидели если объект исключения был возвращен, чтобы определить, произошла ошибка, поэтому этот метод всегда должна возвращать объект исключения, если произошла ошибка.  Строка ошибки должна быть также предоставляется в том случае, если вызывающий объект должен использовать его.  
  
## См. также  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)