---
title: "IDiaStackFrame::get_maxStack | Microsoft Docs"
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
  - "IDiaStackFrame::get_maxStack - метод"
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_maxStack
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает максимальное число байтов отправлянных в стеке во фрейме.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает максимальное число байтов отправлянных в стеке.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)