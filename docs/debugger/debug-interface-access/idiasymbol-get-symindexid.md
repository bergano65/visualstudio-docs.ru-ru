---
title: "IDiaSymbol::get_symIndexId | Microsoft Docs"
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
  - "IDiaSymbol::get_symIndexId - метод"
ms.assetid: dd1fb3ba-31bf-497d-a6bf-79f1206e6642
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_symIndexId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает уникальный идентификатор символов.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_symIndexId (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает идентификатор символов символов.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 Идентификатор уникальное значение, созданное SDK для доступа к интерфейсу отладки, чтобы пометить все символы в виде уникальной.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)