---
title: "IDiaSymbol::get_stride | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4264742a-3d91-44b9-9d14-87adbc77f0f0
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_stride
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает шаг матрицы или strided массива.  
  
## Синтаксис  
  
```cpp  
HRESULT get_stride(   
   DWORD* pRetVal);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] указатель на `DWORD`, содержащего шаг.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)