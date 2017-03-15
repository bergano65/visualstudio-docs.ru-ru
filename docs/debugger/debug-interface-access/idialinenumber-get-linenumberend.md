---
title: "IDiaLineNumber::get_lineNumberEnd | Microsoft Docs"
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
  - "IDiaLineNumber::get_lineNumberEnd - метод"
ms.assetid: b101853e-2bcf-47c1-acef-e13984c7ea9d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_lineNumberEnd
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает смещение номер линии источника, когда оператор или выражение.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_lineNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает номер линии, где оператор или выражение.  Если значение равно нулю, то данные окончания отсутствует.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)