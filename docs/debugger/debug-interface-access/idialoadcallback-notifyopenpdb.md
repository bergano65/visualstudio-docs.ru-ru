---
title: "IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyOpenPDB - метод"
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::NotifyOpenPDB
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Вызывается при открытии выбранного файла pdb.  
  
## Синтаксис  
  
```cpp#  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### Параметры  
 `pdbPath`  
 \[in\] полный путь к pdb\-файлу.  
  
 `resultCode`  
 \[in\] код, который отображает успешное завершение \(`S_OK`\) или сбой загрузки в применении к этому файлу.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Код возврата, обычно не учитывается.  
  
## См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)