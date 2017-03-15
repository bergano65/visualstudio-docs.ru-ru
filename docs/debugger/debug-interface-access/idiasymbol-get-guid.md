---
title: "IDiaSymbol::get_guid | Microsoft Docs"
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
  - "IDiaSymbol::get_guid - метод"
ms.assetid: c02a6c92-f406-4646-82e7-3cd005af900e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_guid
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает глобальный уникальный идентификатор \(GUID\) символов.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_guid (   
   GUID* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает идентификатор GUID символов.  
  
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