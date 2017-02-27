---
title: "IDiaSymbol::get_sizeInUdt | Microsoft Docs"
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
ms.assetid: a82ab896-0185-46a4-b4d5-babfcc660fe1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_sizeInUdt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает размер элемента пользовательского типа.  
  
## Синтаксис  
  
```cpp  
HRESULT get_sizeInUdt(   
   DWORD* pRetVal);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] указатель на `DWORD`, указывающее размер элемента.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)