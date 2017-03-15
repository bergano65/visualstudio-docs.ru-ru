---
title: "IDebugArrayObject::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetRank"
helpviewer_keywords: 
  - "Метод IDebugArrayObject::GetRank"
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает последовательность массивов, т е число измерений.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### Параметры  
 `pdwRank`  
 \[out\] возвращает ряд.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Используйте [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) метод для извлечения размер каждого измерения массива объекта.  
  
## См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)