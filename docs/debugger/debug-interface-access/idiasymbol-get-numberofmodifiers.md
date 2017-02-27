---
title: "IDiaSymbol::get_numberOfModifiers | Microsoft Docs"
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
ms.assetid: 61ff7431-1994-4f7e-a182-1817f16f60a9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_numberOfModifiers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает число модификаторов, которые применяются к исходному типу.  
  
## Синтаксис  
  
```cpp  
HRESULT get_numberOfModifiers(   
   DWORD* pRetVal);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] указатель на `DWORD`, указывающее количество модификаторов, которые применяются к исходному типу.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)