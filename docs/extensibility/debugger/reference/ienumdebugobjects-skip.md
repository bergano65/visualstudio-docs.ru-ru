---
title: "IEnumDebugObjects::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::Skip"
helpviewer_keywords: 
  - "Метод IEnumDebugObjects::Skip"
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumDebugObjects::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод пропустит над заданным количеством элементов.  
  
## Синтаксис  
  
```cpp#  
HRESULT Skip(  
   [in] ULONG celt  
);  
```  
  
```c#  
int Skip(  
   [In] uint celt  
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
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)