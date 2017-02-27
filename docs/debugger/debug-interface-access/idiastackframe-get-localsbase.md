---
title: "IDiaStackFrame::get_localsBase | Microsoft Docs"
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
  - "IDiaStackFrame::get_localsBase - метод"
ms.assetid: eb0bd73e-d92d-468e-a0b1-fbc279919f54
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackFrame::get_localsBase
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает базовый адрес локальные переменные для кадра.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_localsBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает базовый адрес локальных переменных.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)