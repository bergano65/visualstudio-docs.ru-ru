---
title: "IDiaSymbol::get_paramBasePointerRegisterId | Microsoft Docs"
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
  - "IDiaSymbol::get_paramBasePointerRegisterId - метод"
ms.assetid: 9f5caeb4-5c88-4054-bf8b-50d34bbbf8c5
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDiaSymbol::get_paramBasePointerRegisterId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает идентификатор регистра, в котором содержится базовый указатель на параметры.  Используется, если [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) равно  `SymTagFunction`.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_paramBasePointerRegisterId (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает идентификатор регистра, в котором содержится базовый указатель на параметры.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia100.dll  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)