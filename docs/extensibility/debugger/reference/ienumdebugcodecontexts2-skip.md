---
title: "IEnumDebugCodeContexts2::Skip | Microsoft Docs"
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
  - "IEnumDebugCodeContexts2::Skip"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2::Skip"
ms.assetid: 3451a3eb-bf5b-4ec5-acc9-aa5a24363801
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCodeContexts2::Skip
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
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)