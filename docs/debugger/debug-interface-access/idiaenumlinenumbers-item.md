---
title: "IDiaEnumLineNumbers::Item | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Item - метод"
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumLineNumbers::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает номер линии посредством индекса.  
  
## Синтаксис  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### Параметры  
 индекс  
 \[in\] индекс [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) объект, который требуется извлечь.  Индекс в диапазоне от 0 до `count`\-1, где  `count` возвращает   [IDiaEnumLineNumbers::get\_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) метод.  
  
 lineNumber  
 \[out\] возвращает [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) объект, представляющий нужный номер линии.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)