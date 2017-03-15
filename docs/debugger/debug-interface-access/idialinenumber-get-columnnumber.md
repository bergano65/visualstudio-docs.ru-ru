---
title: "IDiaLineNumber::get_columnNumber | Microsoft Docs"
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
  - "IDiaLineNumber::get_columnNumber - метод"
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_columnNumber
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает номер столбца, в котором начинается выражение или оператор.  
  
## Синтаксис  
  
```  
[C++]  
HRESULT get_columnNumber (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает номер столбца, в котором начинается выражение или оператор.  Если значение равно нулю, то данные столбца отсутствует.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Значение столбца, возвращенное этим методом, смещение байта в линии до первого символа выписки на линии.  
  
## См. также  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)