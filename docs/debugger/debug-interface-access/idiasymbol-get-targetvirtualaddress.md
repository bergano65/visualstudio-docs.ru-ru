---
title: "IDiaSymbol::get_targetVirtualAddress | Microsoft Docs"
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
  - "IDiaSymbol::get_targetVirtualAddress - метод"
ms.assetid: a0a5ce72-95f8-443e-bb4b-8c21194faad0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSymbol::get_targetVirtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает виртуальный адрес \(VA\) целевого объекта преобразователя.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_targetVirtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает VA целевого объекта преобразователя.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 Это свойство допустимо только в том случае, если символ как a [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значение   `SymTagThunk`.  
  
 "Type" часть кода, который выполняет преобразование между 32 пробелом адреса памяти \(также известной как плоское адресное пространство\) и шестнадцатиразрядным местом для адреса \(называемый поделенное на сегменты адресное пространство\).  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)