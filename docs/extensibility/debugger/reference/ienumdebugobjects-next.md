---
title: "IEnumDebugObjects::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::Next"
helpviewer_keywords: 
  - "Метод IEnumDebugObjects::Next"
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugObjects::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает следующий набор элементов перечисления.  
  
## Синтаксис  
  
```cpp#  
HRESULT Next(  
   ULONG          celt,  
   IDebugObject** rgelt,  
   ULONG*         pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint           celt,  
   IDebugObject[] rgelt,  
   ref uint       pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число элементов, которые нужно получить.  Также определяет максимальный размер `rgelt` массив.  
  
 `rgelt`  
 \[in, out\] массив IDebugObject элементы, которые требуется заполнить.  
  
 `pceltFetched`  
 \[out\] возвращает число элементов, фактически возвращенных в пределах `rgelt`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если меньше, чем количество запрошенных элементов могут быть возвращены. в противном случае возвращает код ошибки.  
  
## См. также  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)