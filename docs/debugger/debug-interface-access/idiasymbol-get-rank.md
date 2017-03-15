---
title: "IDiaSymbol::get_rank | Microsoft Docs"
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
  - "IDiaSymbol::get_rank - метод"
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает последовательность \(число измерений\) многомерный массив FORTRAN.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает количество измерений в многомерный массив FORTRAN.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 Последовательность называют число измерений в массиве, в котором массив объявляется как `myarray[1,2,3]`.  В этом примере имеется ряд 3 и 3 измерений.  Ряды не применяется к C\+\+, использующее понятие массива массивов для каждого измерения \(т е `myarray[1][2][3]`\).  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)