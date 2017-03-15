---
title: "IDiaSourceFile::get_fileName | Microsoft Docs"
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
  - "IDiaSourceFile::get_fileName - метод"
ms.assetid: a5cb8927-23c6-469e-8f78-f2787d85dba4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSourceFile::get_fileName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает имя файла источника.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_fileName (   
   BSTR* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает имя файла источника.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)