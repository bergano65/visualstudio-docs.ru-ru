---
title: "IDiaStackFrame::get_systemExceptionHandling | Microsoft Docs"
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
  - "IDiaStackFrame::get_systemExceptionHandling"
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_systemExceptionHandling
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить, указывающее, является ли обработка ошибок системы.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_systemExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает `TRUE` если обработка ошибок системы, действующих для данного кадра; в противном случае возвращает  `FALSE`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Обработка ошибок системы также называется структурная обработка исключений.  Это не является один и тот же действия, как обработка исключений С\+\+.  
  
 Чтобы определить, что обработка исключений С\+\+ в силе, вызовите [IDiaStackFrame::get\_cplusplusExceptionHandling](../Topic/IDiaStackFrame::get_cplusplusExceptionHandling.md) метод.  
  
## См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackFrame::get\_cplusplusExceptionHandling](../Topic/IDiaStackFrame::get_cplusplusExceptionHandling.md)