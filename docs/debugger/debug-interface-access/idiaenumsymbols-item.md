---
title: "IDiaEnumSymbols::Item | Microsoft Docs"
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
  - "IDiaEnumSymbols::Item - метод"
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbols::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает символ посредством индекса.  
  
## Синтаксис  
  
```cpp#  
HRESULT Item (   
   DWORD        index,  
   IDiaSymbol** symbol  
);  
```  
  
#### Параметры  
 индекс  
 \[in\] индекс [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, который требуется извлечь.  Индекс в диапазоне от 0 до `count`\-1, где  `count` возвращает   [IDiaEnumSymbols::get\_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) метод.  
  
 symbol  
 \[out\] возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий нужный символ.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)