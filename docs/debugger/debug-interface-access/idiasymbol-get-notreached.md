---
title: "IDiaSymbol::get_notReached | Microsoft Docs"
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
  - "IDiaSymbol::get_notReached - метод"
ms.assetid: e44ba922-6cda-40c2-9b62-44e5a8628e63
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_notReached
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить который определяет, является ли функция не достигаются или метка никогда.  
  
## Синтаксис  
  
```cpp  
HRESULT get_notReached(  
   BOOL *pFlag  
);  
```  
  
#### Параметры  
 pFlag  
 \[out\] возвращает `TRUE` если функция или метка никогда не достигаются; в противном случае возвращает  `FALSE`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Требования  
  
|Требование|Описание|  
|----------------|--------------|  
|Заголовок:|dia2.h|  
|Версия:|Пакет SDK для доступа к интерфейсу отладки v8.0|  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)