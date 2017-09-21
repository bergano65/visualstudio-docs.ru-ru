---
title: "IEnumCodePaths2::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2::Clone"
helpviewer_keywords: 
  - "IEnumCodePaths2::Clone"
ms.assetid: 9d5c6bc6-7e72-4f1b-801c-7192458f3ba8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumCodePaths2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает копию текущего перечисления как отдельный объект.  
  
## Синтаксис  
  
```cpp#  
HRESULT Clone(  
   IEnumCodePaths2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumCodePaths2 ppEnum  
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
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)