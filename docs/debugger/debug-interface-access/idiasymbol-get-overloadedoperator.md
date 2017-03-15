---
title: "IDiaSymbol::get_overloadedOperator | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaSymbol::get_overloadedOperator - метод"
ms.assetid: 257a9894-e980-47ae-bdc0-c5e2293ea734
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_overloadedOperator
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить, указывающий перегруженный ли определяемый пользователем тип данных.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_overloadedOperator (   
   BOOL* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает `TRUE` если определяемый пользователем тип данных перегруженный операторы; в противном случае возвращает  `FALSE`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)