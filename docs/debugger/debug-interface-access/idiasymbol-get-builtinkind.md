---
title: "IDiaSymbol::get_builtInKind | Microsoft Docs"
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
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_builtInKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает встроенный тип HLSL.  
  
## Синтаксис  
  
```cpp  
HRESULT get_buildInKind(   
   DWORD* pRetVal);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] указатель на `DWORD`, который содержит встроенный тип HLSL.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)