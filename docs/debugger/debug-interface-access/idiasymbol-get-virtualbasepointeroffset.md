---
title: "IDiaSymbol::get_virtualBasePointerOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualBasePointerOffset - метод"
ms.assetid: a4f2649c-6702-491c-90a1-d6d669258c51
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_virtualBasePointerOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает смещение виртуального базового указателя.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_virtualBasePointerOffset (   
   LONG* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает смещение виртуального базового указателя.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)