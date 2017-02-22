---
title: "IEnumDebugCodeContexts2::Next | Microsoft Docs"
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
  - "IEnumDebugCodeContexts2::Next"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2::Next"
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCodeContexts2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает следующий набор элементов перечисления.  
  
## Синтаксис  
  
```cpp#  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext2** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                 celt,  
   IDebugCodeContext2[] rgelt,  
   ref uint             pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число элементов, которые нужно получить.  Также определяет максимальный размер `rgelt` массив.  
  
 `rgelt`  
 \[in, out\] массив IDebugCodeContext2 элементы, которые требуется заполнить.  
  
 `pceltFetched`  
 \[out\] возвращает число элементов, фактически возвращенных в пределах `rgelt`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если меньше, чем количество запрошенных элементов могут быть возвращены. в противном случае возвращает код ошибки.  
  
## См. также  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)