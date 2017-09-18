---
title: "IEnumDebugErrorBreakpoints2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugErrorBreakpoints2::Next"
helpviewer_keywords: 
  - "IEnumDebugErrorBreakpoints2::Next"
ms.assetid: 6a3dee11-5267-4d77-9e28-6a38413ba70b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugErrorBreakpoints2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает следующий набор элементов перечисления.  
  
## Синтаксис  
  
```cpp#  
HRESULT Next(  
   ULONG                    celt,  
   IDebugErrorBreakpoint2** rgelt,  
   ULONG*                   pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                     celt,  
   IDebugErrorBreakpoint2[] rgelt,  
   ref uint                 pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число элементов, которые нужно получить.  Также определяет максимальный размер `rgelt` массив.  
  
 `rgelt`  
 \[in, out\] массив IDebugErrorBreakpoint2 элементы, которые требуется заполнить.  
  
 `pceltFetched`  
 \[out\] возвращает число элементов, фактически возвращенных в пределах `rgelt`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если меньше, чем количество запрошенных элементов могут быть возвращены. в противном случае возвращает код ошибки.  
  
## См. также  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)