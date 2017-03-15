---
title: "IDiaEnumTables::get_Count | Microsoft Docs"
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
  - "IDiaEnumTables::get_Count - метод"
ms.assetid: 30fa316b-a746-4028-acae-4efcd2066f38
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumTables::get_Count
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает количество таблиц.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_Count (    LONG* pRetVal  
);  
  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает число таблиц.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)