---
title: "IDiaSegment::get_offset | Microsoft Docs"
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
  - "IDiaSegment::get_offset - метод"
ms.assetid: 97415ac6-b072-4e3c-9dd3-73087ae605fc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSegment::get_offset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает смещение в сегментах, где раздел.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_offset (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает смещение в сегментах, где раздел.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)