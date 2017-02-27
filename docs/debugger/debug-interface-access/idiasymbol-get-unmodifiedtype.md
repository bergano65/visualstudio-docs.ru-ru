---
title: "IDiaSymbol::get_unmodifiedType | Microsoft Docs"
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
  - "IDiaSymbol::get_unmodifiedType - метод"
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_unmodifiedType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает исходный тип для этого символа.  Используется, если [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) присваивается типу.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий исходный тип этого символа.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 Текущий тип изменение возвращенного исходного типа.  Исходный тип для символов может быть определен первым получение символьный тип, а затем опрашивать то возвращаемый тип для исходного типа.  Обратите внимание, что некоторые символы не могут иметь измененный тип исходного типа.  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia100.dll  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)