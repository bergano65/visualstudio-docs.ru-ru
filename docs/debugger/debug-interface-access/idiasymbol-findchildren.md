---
title: "IDiaSymbol::findChildren | Microsoft Docs"
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
  - "IDiaSymbol::findChildren - метод"
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает дочерние элементы символов.  
  
## Синтаксис  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Параметры  
 `symtag`  
 \[in\] задает теги символов дочерних элементов, которые нужно извлечь, как определено в [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md).  Значение `SymTagNull` для всех дочерних элементов, которые необходимо извлечь.  
  
 `name`  
 \[in\] определяет имя дочерних элементов, которые необходимо извлечь.  Значение `NULL` для всех дочерних элементов, которые необходимо извлечь.  
  
 `compareFlags`  
 \[in\] определяет параметры сравнения, применяемые для именования совпадать.  Значения [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) перечисление можно использовать по отдельности или в сочетании.  
  
 `ppResult`  
 \[out\] возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) объект, содержащий список полученных символов дочернего элемента.  
  
## Возвращаемое значение  
 Возвращает `S_OK` если хотя бы один дочерний элемент был найден или возвращает символов  `S_FALSE` если дочерние элементы не были найдены. в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод идентичен вызову [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) метод с этим символом как первый параметр.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)