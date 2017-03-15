---
title: "IDiaSectionContrib::get_addressSection | Microsoft Docs"
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
  - "IDiaSectionContrib::get_addressSection - метод"
ms.assetid: 13fe7e0b-c978-4a1d-bb57-64c8583b5e14
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSectionContrib::get_addressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает часть раздела адреса вклада.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает часть раздела адреса вклада.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)