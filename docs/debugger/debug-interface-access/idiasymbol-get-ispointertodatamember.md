---
title: "IDiaSymbol::get_isPointerToDataMember | Microsoft Docs"
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
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isPointerToDataMember
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает, является ли этот символ указатель к элементу данных.  
  
## Синтаксис  
  
```cpp  
HRESULT get_isPointerToDataMember(   
   BOOL* pRetVal);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] указатель на `BOOL`, который указывает, является ли этот символ указатель к элементу данных.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)