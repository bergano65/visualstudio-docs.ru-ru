---
title: "IDiaSymbol::get_pure | Microsoft Docs"
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
  - "IDiaSymbol::get_pure - метод"
ms.assetid: b61107e9-9144-4981-b7ef-58a339b80c58
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_pure
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить который определяет, является ли функция чисто виртуальный.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_pure (   
   BOOL* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает `TRUE` если функция чисто виртуальный; в противном случае возвращает  `FALSE`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)