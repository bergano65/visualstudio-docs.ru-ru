---
title: "IDiaSymbol::get_thunkOrdinal | Microsoft Docs"
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
  - "IDiaSymbol::get_thunkOrdinal - метод"
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает тип преобразователя функции.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает значение [Перечисление THUNK\_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) перечисление, определяющее тип преобразователя функции.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 Это свойство допустимо только в том случае, если символ как a [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значение   `SymTagThunk`.  
  
 "Type" часть кода, который выполняет преобразование между 32 пробелом адреса памяти \(также известной как плоское адресное пространство\) и шестнадцатиразрядным местом для адреса \(называемый поделенное на сегменты адресное пространство\).  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление THUNK\_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)