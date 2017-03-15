---
title: "IDiaSegment::get_virtualAddress | Microsoft Docs"
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
  - "IDiaSegment::get_virtualAddress - метод"
ms.assetid: 30073dd0-c864-4c4a-8863-80f243419f6c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSegment::get_virtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает виртуальный адрес \(\) VA начальной секции.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает VA начала раздела.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)