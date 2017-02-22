---
title: "IDebugMemoryBytes2::ReadAt | Microsoft Docs"
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
  - "IDebugMemoryBytes2::ReadAt"
helpviewer_keywords: 
  - "Метод IDebugMemoryBytes2::ReadAt"
  - "Метод ReadAt"
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Считывает последовательность байтов, начиная с заданной позиции.  
  
## Синтаксис  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```c#  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### Параметры  
 `pStartContext`  
 \[in\] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объект, который указывает расположение начала байты чтения.  
  
 `dwCount`  
 \[in\] число байтов для чтения.  Также определяет длину  `rgbMemory` массив.  
  
 `rgbMemory`  
 \[in, out\] массив байтов, считанных в действительности залитый с.  
  
 `pdwRead`  
 \[out\] возвращает число последовательных фактически считанных байтов.  
  
 `pdwUnreadable`  
 \[in, out\] возвращает число нечитабельных байтов.  Может иметь значение NULL, если клиент незаинтересован в количестве нечитабельных байтов.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Если запрашивается и первые 50 100 байт для чтения, то следующие 20 нечитабельно, а оставшиеся 30 для чтения, этот метод возвращает:  
  
 \*`pdwRead` \= 50  
  
 \*`pdwUnreadable` \= 20  
  
 В этом случае, поскольку `*pdwRead + *pdwUnreadable < dwCount`вызывающий объект должен вызвать дополнительный для считывания оставшиеся 30 байтов исходной и запрошенного 100  [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объект, передаваемый в  `pStartContext` параметр должен быть перемещен 70.  
  
## См. также  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)