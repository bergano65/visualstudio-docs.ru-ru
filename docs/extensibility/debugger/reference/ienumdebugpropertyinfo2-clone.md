---
title: "IEnumDebugPropertyInfo2::Clone | Microsoft Docs"
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
  - "IEnumDebugPropertyInfo2::Clone"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2::Clone"
ms.assetid: 0ede1667-1071-4aa4-b887-260ea103d724
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPropertyInfo2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает копию текущего перечисления как отдельный объект.  
  
## Синтаксис  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugPropertyInfo2 ppEnum  
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
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)