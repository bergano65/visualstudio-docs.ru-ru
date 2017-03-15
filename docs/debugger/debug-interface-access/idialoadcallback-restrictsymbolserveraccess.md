---
title: "IDiaLoadCallback::RestrictSymbolServerAccess | Microsoft Docs"
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
  - "IDiaLoadCallback::RestrictSymbolServerAccess - метод"
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::RestrictSymbolServerAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Определяет, разрешен доступ к серверу символов к символам решения.  
  
## Синтаксис  
  
```cpp#  
HRESULT RestrictSymbolServerAccess();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Любой код возврата, отличный от `S_OK` предотвращает использование сервера символов для разрешения символов.  
  
## См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)