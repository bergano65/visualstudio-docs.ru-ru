---
title: "IEnumDebugBoundBreakpoints2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugBoundBreakpoints2::Skip"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2::Skip"
ms.assetid: 95659709-6d7c-44ca-b598-629eb688429f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEnumDebugBoundBreakpoints2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Скипы над заданным количеством элементов.  
  
## Синтаксис  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число элементов, которые нужно пропустить.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` If  `celt` большее число оставшихся элементов; в противном случае возвращает код ошибки.  
  
## Заметки  
 If `celt` определяет значение, превышающее число оставшихся элементов набора в конец и перечисление  `S_FALSE` возвращает.  
  
## См. также  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)