---
title: Басиктипе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580841"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает базовый тип символа.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="elements"></a>Элементы  
 бтнотипе  
 Базовый тип не указан.  
  
 бтвоид  
 Базовый тип — `void` .  
  
 бтчар  
 Базовый тип — это `char` тип (C/C++).  
  
 бтвчар  
 Базовый тип — это широкий символ (в Юникоде) ( `WCHAR` ).  
  
 бтинт  
 Базовый тип — `signed int` (тип C/C++).  
  
 бтуинт  
 Базовый тип — `unsigned int` (тип C/C++).  
  
 бтфлоат  
 Базовый тип — число с плавающей запятой ( `FLOAT` ).  
  
 бтбкд  
 Базовый тип — это двоично-кодированное десятичное число ( `BCD` ).  
  
 бтбул  
 Базовый тип — логическое значение ( `BOOL` ).  
  
 бтлонг  
 Базовый тип — это `long int` тип (C/C++).  
  
 бтулонг  
 Базовый тип — это `unsigned long int` тип (C/C++).  
  
 бткурренци  
 Базовый тип — Currency.  
  
 бтдате  
 Базовый тип — Дата и время ( `DATE` ).  
  
 бтвариант  
 Базовый тип — это структура типа переменной ( `VARIANT` ).  
  
 бткомплекс  
 Базовый тип — комплексное число.  
  
 бтбит  
 Тип "базовый" является битом.  
  
 бтбстр  
 Базовый тип — это базовая или двоичная строка ( `BSTR` ).  
  
 бсресулт  
 Базовый тип — `HRESULT` .  
  
## <a name="remarks"></a>Remarks  
 Значения в этом перечислении возвращаются методом [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
