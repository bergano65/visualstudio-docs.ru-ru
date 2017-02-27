---
title: "IDiaEnumSymbolsByAddr::Prev | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Prev - метод"
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает предыдущие символы в порядке адресом.  
  
## Синтаксис  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### Параметры  
 celt  
 \[in\] количество символов в перечислителе.  
  
 rgelt  
 \[out\] массив, которые можно заполнять с [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекты, представляющие нужных символов.  
  
 pceltFetched  
 \[out\] возвращает число символов в выборке перечислителе.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если предыдущие символы.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод обновляет позиция перечислителя количеством извлеченных элементов.  
  
## См. также  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)