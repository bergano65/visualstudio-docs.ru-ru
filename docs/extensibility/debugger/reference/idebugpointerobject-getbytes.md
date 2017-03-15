---
title: "IDebugPointerObject::GetBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::GetBytes"
helpviewer_keywords: 
  - "Метод IDebugPointerObject::GetBytes"
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает значение указанно на ряд последовательных как байтов.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### Параметры  
 `dwStart`  
 \[in\] смещение в байтах от начала объекта указало.  
  
 `dwCount`  
 \[in\] количество байтов, которое необходимо извлечь.  
  
 `pBytes`  
 \[in, out\] массив, который заполняется с значением ряд последовательных байтов, начиная с заданного смещения из объекта указал значение.  
  
 `pdwBytes`  
 \[out\] возвращает число фактически полученных байтов.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод используется, если указатель в виде данным IDebugPointerObject указывает на тип\-примитиву или простой массив простых типов \(то есть массива, который может быть представлен простой последовательностью байтов\).  
  
## См. также  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)