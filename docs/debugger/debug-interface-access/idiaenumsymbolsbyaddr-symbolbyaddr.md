---
title: "IDiaEnumSymbolsByAddr::symbolByAddr | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::symbolByAddr - метод"
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumSymbolsByAddr::symbolByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Перемещает перечислитель, выполнив поиск по номеру и смещением раздела образа.  
  
## Синтаксис  
  
```cpp#  
HRESULT symbolByAddr (   
   DWORD**      isect,  
   DWORD**      offsect,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### Параметры  
 isect  
 \[in\] номер секции образа.  
  
 offsect  
 \[in\] смещение в разделе.  
  
 ppsymbol  
 \[out\] возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий найденный знак.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если символ не может быть найден.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)