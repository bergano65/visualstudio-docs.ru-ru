---
title: "IDiaSymbol::findChildrenExByAddr | Microsoft Docs"
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
  - "IDiaSymbol::findChildrenExByAddr"
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::findChildrenExByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает дочерние элементы символов, допустимых по указанному адресу.  
  
## Синтаксис  
  
```cpp#  
HRESULT findChildrenExByAddr (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Параметры  
 `symtag`  
 \[in\] задает теги символов дочерних элементов, которые нужно извлечь, как определено в [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md).  Значение `SymTagNull` для всех дочерних элементов, которые необходимо извлечь.  
  
 `name`  
 \[in\] определяет имя дочерних элементов, которые необходимо извлечь.  Значение `NULL` для всех дочерних элементов, которые необходимо извлечь.  
  
 `compareFlags`  
 \[in\] определяет параметры сравнения, применяемых для именования совпадать.  Значения [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) перечисление можно использовать по отдельности или в сочетании.  
  
 `address`  
 \[in\] адрес символов.  
  
 `ppResult`  
 \[out\] возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) объект, содержащий список полученных символов дочернего элемента.  
  
## Возвращаемое значение  
 Возвращает `S_OK` если хотя бы один дочерний элемент был найден или возвращает символов  `S_FALSE` если дочерние элементы не были найдены. в противном случае возвращает код ошибки.  
  
## Заметки  
 Локальные символы, которые возвращаются включают данные в режиме реального времени диапазона.  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia100.dll  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)