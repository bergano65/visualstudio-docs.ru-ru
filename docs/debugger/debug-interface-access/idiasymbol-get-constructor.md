---
title: "IDiaSymbol::get_constructor | Microsoft Docs"
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
  - "IDiaSymbol::get_constructor - метод"
ms.assetid: 2f2cf1e0-f817-4ca0-b782-3341362c46a9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_constructor
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить, указывающее, имеет ли определяемый пользователем тип данных конструктора или деструктора.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_constructor (   
   BOOL* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает `TRUE` если определяемый пользователем тип данных имеет конструктора или деструктора; в противном случае возвращает  `FALSE`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Требования  
  
|Требование|Описание|  
|----------------|--------------|  
|Заголовок:|dia2.h|  
|Версия:|Пакет SDK для доступа к интерфейсу отладки v7.0|  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)