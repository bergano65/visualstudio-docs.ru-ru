---
title: "IEnumDebugPorts2::Clone | Microsoft Docs"
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
  - "IEnumDebugPorts2::Clone"
helpviewer_keywords: 
  - "IEnumDebugPorts2::Clone"
ms.assetid: d5ce77e8-bb99-409a-98fa-20fe5a0de25e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPorts2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает копию текущего перечисления как отдельный объект.  
  
## Синтаксис  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### Параметры  
 `ppEnum`  
 \[out\] возвращает копию данного перечисления как отдельный объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Копия перечисления имеет одно и то же состояние, как исходные в момент вызова этого метода.  Однако копии и состояния исходного отдельно и могут быть изменены по отдельности.  
  
## См. также  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)