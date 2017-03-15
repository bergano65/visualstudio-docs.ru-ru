---
title: "IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictOriginalPathAccess - метод"
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Определяет, если он одобрен найти pdb\-файл в оригинале каталог отладки.  
  
## Синтаксис  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Любой код возврата, отличный от `S_OK` предотвращает найти pdb\-файл в оригинале каталог отладки.  Исходный каталог отладки путь к файлу символов отладки включит компилированному в исполняемый файл.  Этот путь не обязательно этого же, как путь, где исполняемый файл существует.  
  
## См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)