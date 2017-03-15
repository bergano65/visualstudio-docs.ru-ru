---
title: "IDiaLoadCallback2::RestrictDBGAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictDBGAccess - метод"
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaLoadCallback2::RestrictDBGAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Определяет, если поиск отладочной информации позволяет из файлов .dbg.  
  
## Синтаксис  
  
```cpp#  
HRESULT RestrictDBGAccess();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Любое возвращаемое значение, отличное от `S_OK` для предотвращения поиск отладочной информации из файлов .dbg.  
  
## См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)