---
title: "IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadULONGLONG"
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Считывает `ULONGLONG` значения в наборе свойств.  
  
## Синтаксис  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### Параметры  
 `id`  
 \[in\] идентификатор свойства, которое необходимо считать \(`PROPID` определяет, а в WTypes.h  `ULONG`\).  
  
 `pValue`  
 \[out\] возвращает значение свойства.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_INVALIDARG` если свойство не принадлежит к типу  `ULONGLONG`.  
  
## Заметки  
 A `ULONGLONG` определяет окнами как 64 целое число без знака.  
  
## См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)