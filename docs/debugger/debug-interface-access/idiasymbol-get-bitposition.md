---
title: "IDiaSymbol::get_bitPosition | Microsoft Docs"
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
  - "IDiaSymbol::get_bitPosition - метод"
ms.assetid: b0059407-8655-497b-81ca-025595989371
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_bitPosition
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает положение бита расположения.  Используется, если [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) существует  `LocIsBitField`.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_bitPosition (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает положение бита расположения.  
  
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
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)