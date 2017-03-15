---
title: "IDiaPropertyStorage::ReadLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadLONG"
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Считывает `LONG` значения в наборе свойств.  
  
## Синтаксис  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### Параметры  
 `id`  
 \[in\] идентификатор свойства, которое необходимо считать \(`PROPID` определяет, а в WTypes.h  `ULONG`\).  
  
 `pValue`  
 \[out\] возвращает значение свойства.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_INVALIDARG` если свойство не принадлежит к типу  `LONG`.  
  
## Заметки  
 A `LONG` определяет окнами как 32 знаковое целое число.  
  
## См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)