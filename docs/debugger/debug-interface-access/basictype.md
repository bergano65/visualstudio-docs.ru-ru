---
title: "BasicType | Microsoft Docs"
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
  - "BasicType - перечисление"
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# BasicType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает символьный тип основной.  
  
## Синтаксис  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## Elements  
 btNoType  
 Отсутствует базовый тип не определен.  
  
 btVoid  
 Базовый тип a `void`.  
  
 btChar  
 Базовый тип a `char` \(Тип C\/C\+\+\).  
  
 btWChar  
 Базовый тип широкий символ \(юникод\) \(`WCHAR`\).  
  
 btInt  
 Базовый тип `signed int` \(Тип C\/C\+\+\).  
  
 btUInt  
 Базовый тип `unsigned int` \(Тип C\/C\+\+\).  
  
 btFloat  
 Базовый тип число с плавающей запятой \("`FLOAT`\).  
  
 btBCD  
 Базовый тип binary\-закодированное десятичное число \(`BCD`\).  
  
 btBool  
 Логическое \(базовый тип`BOOL`\).  
  
 btLong  
 Базовый тип a `long int` \(Тип C\/C\+\+\).  
  
 btULong  
 Базовый тип `unsigned long int` \(Тип C\/C\+\+\).  
  
 btCurrency  
 Базовый тип валюта.  
  
 btDate  
 Базовый тип даты и времени \(`DATE`\).  
  
 btVariant  
 Базовый тип переменной типа \(структура`VARIANT`\).  
  
 btComplex  
 Базовый тип комплексное число.  
  
 btBit  
 Базовый тип bit.  
  
 btBSTR  
 Базовый тип главной или бинарная строка \(`BSTR`\).  
  
 btHresult  
 Базовый тип `HRESULT`.  
  
## Заметки  
 В этом перечислении возвращаемые значения [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) метод.  
  
## Требования  
 Заголовок: cvconst.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)