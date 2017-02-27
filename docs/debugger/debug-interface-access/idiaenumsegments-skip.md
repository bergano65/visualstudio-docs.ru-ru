---
title: "IDiaEnumSegments::Skip | Microsoft Docs"
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
  - "IDiaEnumSegments::Skip - метод"
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Пропустить указанное количество сегментов в последовательности перечисления.  
  
## Синтаксис  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Параметры  
 celt  
 \[in\] количество сегментов в последовательности перечисления, которые нужно пропустить.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` если больше сегментов, которые нужно пропустить.  
  
## См. также  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)