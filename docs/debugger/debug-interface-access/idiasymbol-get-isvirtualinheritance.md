---
title: "IDiaSymbol::get_isVirtualInheritance | Microsoft Docs"
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
ms.assetid: 72906b92-dd4a-42e3-9b24-b77628fa48c1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isVirtualInheritance
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Определяет, является ли точки указателя `this` к элементу данных с виртуальным наследованием.  
  
## Синтаксис  
  
```cpp  
HRESULT get_isVirtualInheritance(   
   BOOL* pRetVal);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] указатель на `BOOL`, который определяет, предшествует ли указатель `this` к элементу данных с виртуальным наследованием.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)