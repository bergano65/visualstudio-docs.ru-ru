---
title: "IDiaSectionContrib::get_relocationsCrc | Microsoft Docs"
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
  - "IDiaSectionContrib::get_relocationsCrc - метод"
ms.assetid: 8c29c91a-062d-4566-a9b7-49251036a15a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSectionContrib::get_relocationsCrc
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает циклическую проверку избыточности \(CRC\) перемещения данных для секции.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_relocationsCrc (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает CRC данных перемещения для секции.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)