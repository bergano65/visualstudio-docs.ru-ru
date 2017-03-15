---
title: "IDiaSymbol::get_addressOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_addressOffset - метод"
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_addressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает часть смещения положения адреса.  Используется, если [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) равно  `LocIsStatic`.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает часть смещения положения адреса.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 Для статических элементов, расположенных во внешнем библиотеки DLL, возвращенное смещение этим методом может быть равен 0, так как этот метод использует получение виртуальный адрес члена.  Допустимо, только если виртуальные адреса [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) метод  [IDiaSession](../../debugger/debug-interface-access/idiasession.md) был вызван интерфейс с ненулевой параметр, задающий адрес загрузки библиотеки DLL.  
  
 Для получения части раздела адреса, вызовите [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) метод.  
  
## Требования  
  
|Требование|Описание|  
|----------------|--------------|  
|Заголовок:|dia2.h|  
|Версия:|Пакет SDK для доступа к интерфейсу отладки v7.0|  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)