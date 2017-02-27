---
title: "IDiaSectionContrib::get_dataCrc | Microsoft Docs"
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
  - "IDiaSectionContrib::get_dataCrc - метод"
ms.assetid: 33b7488f-dc9c-47b3-b08c-737e0eb1bf7d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSectionContrib::get_dataCrc
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает циклическую проверку избыточности \(CRC\) данных в шаге.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_dataCrc (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает CRC данных на шаге.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)