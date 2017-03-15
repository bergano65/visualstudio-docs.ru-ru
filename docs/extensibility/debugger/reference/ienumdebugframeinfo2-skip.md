---
title: "IEnumDebugFrameInfo2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2::Skip"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2::Skip"
ms.assetid: 68cd3948-022a-41ad-bd9f-9ab776cf6248
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugFrameInfo2::Skip
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
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)