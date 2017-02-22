---
title: "IDebugPointerObject::SetBytes | Microsoft Docs"
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
  - "IDebugPointerObject::SetBytes"
helpviewer_keywords: 
  - "Метод IDebugPointerObject::SetBytes"
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Устанавливает значение указанно из серии последовательных байтов.  
  
## Синтаксис  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### Параметры  
 `dwStart`  
 \[in\] смещение в байтах от начала объекта указало.  
  
 `dwCount`  
 \[in\] число байтов, которое необходимо установить.  
  
 `pBytes`  
 \[in\] массив байтов, представляющий новое значение.  Это значение хранится в объекте, начиная с заданного смещения.  
  
 `pdwBytes`  
 \[out\] возвращает число фактически набора байтов.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод используется, если указатель в виде данным IDebugPointerObject указывает на тип\-примитиву или простой массив простых типов \(то есть массива, который может быть представлен простой последовательностью байтов\).  This `IDebugPointerObject` объект не может быть пустой ссылкой \(он должен указывать на адрес в памяти\).  
  
## См. также  
 [Метод GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)