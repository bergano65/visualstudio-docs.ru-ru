---
title: "IEnumDebugCustomAttributes::Next | Microsoft Docs"
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
  - "IEnumCustomAttributes::Next"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::Next"
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCustomAttributes::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Извлекает заданное количество настраиваемых атрибутов в последовательности перечисления.  
  
## Синтаксис  
  
```cpp#  
HRESULT Next (   
   ULONG      celt,  
   CODE_PATH* rgelt,  
   ULONG*     pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                        celt,   
   out IDebugCustomAttribute[] rgelt,   
   ref uint                    pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число элементов, которые нужно получить.  Также определяет максимальный размер `rgelt` массив.  
  
 `rgelt`  
 \[out\] массив [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) объекты, которые требуется заполнить.  
  
 `pceltFetched`  
 \[out\] возвращает число элементов, фактически возвращенных в пределах `rgelt`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если меньше, чем количество запрошенных элементов могут быть возвращены. в противном случае возвращает код ошибки.  
  
## См. также  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)