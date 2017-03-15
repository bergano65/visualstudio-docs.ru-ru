---
title: "IEnumDebugFields::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::Clone"
helpviewer_keywords: 
  - "Метод IEnumDebugFields::Clone"
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugFields::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает копию текущего перечисления как отдельный объект.  
  
## Синтаксис  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Параметры  
 `ppEnum`  
 \[out\] возвращает копию данного перечисления как отдельный объект.  
  
## Значение свойства или возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Копия перечисления имеет одно и то же состояние, как исходные в момент вызова этого метода.  Однако копии и состояния исходного отдельно и могут быть изменены по отдельности.  
  
## См. также  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)