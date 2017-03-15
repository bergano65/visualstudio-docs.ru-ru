---
title: "IDiaEnumSymbolsByAddr::symbolByVA | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::symbolByVA - метод"
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumSymbolsByAddr::symbolByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Перемещает перечислитель, выполняя поиск виртуальным адресом \(VA\).  
  
## Синтаксис  
  
```cpp#  
HRESULT symbolByVA (   
   DWORD**      virtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### Параметры  
 virtualAddress  
 \[in\] виртуальный адрес.  
  
 ppsymbol  
 \[out\] возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий найденный знак.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если символ не может быть найден.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)