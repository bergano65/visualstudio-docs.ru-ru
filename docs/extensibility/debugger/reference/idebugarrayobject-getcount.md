---
title: "IDebugArrayObject::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetCount"
helpviewer_keywords: 
  - "Метод IDebugArrayObject::GetCount"
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает число элементов в массиве.  
  
## Синтаксис  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### Параметры  
 `pdwElements`  
 \[out\] возвращает число.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод видит любые элементы объекта массива как одномерный массив, даже если объект массива является многомерным.  Например, если массив `myarray[3][2][6]`этот метод вернул бы 36  `pdwElements` параметр.  Используйте [GetElement](../Topic/IDebugArrayObject::GetElement.md) метод, чтобы извлечь отдельные элементы поочередно.  
  
## См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)