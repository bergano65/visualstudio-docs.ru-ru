---
title: "IDiaLineNumber::get_addressSection | Microsoft Docs"
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
  - "IDiaLineNumber::get_addressSection - метод"
ms.assetid: a01c1bae-04b2-4c30-8621-60939a3124c2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_addressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает часть раздела адреса памяти, где начинается блок.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 pRetVal  
 \[out\] возвращает часть раздела адреса памяти, где начинается блок.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## Пример  
  
```cpp#  
CComPtr< IDiaLineNumber > pLine;  
DWORD seg;  
pLine->get_addressSection( &seg );  
```  
  
## См. также  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaLineNumber::get\_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)