---
title: "IDebugArrayObject::GetDimensions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetDimensions"
helpviewer_keywords: 
  - "Метод IDebugArrayObject::GetDimensions"
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает измерения массива.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```c#  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### Параметры  
 `dwCount`  
 \[in\] размерность, который необходимо извлечь.  
  
 `dwDimensions`  
 \[in, out\] массив, который заполняется с размерами каждого измерения.  `dwCount` определяет максимальный размер  `dwDimensions` массив.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Многомерный массив может иметь различные размеры для каждого измерения.  Например, если трехмерный массив `myarray[3][2][6]`этот метод вернул бы 3, 2 и 6  `dwDimensions` параметр в указанном порядке.  
  
## См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)