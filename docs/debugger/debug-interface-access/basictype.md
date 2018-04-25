---
title: BasicType | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfccb444eab802f7caa5cf83faff0ddc7a51c389
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="basictype"></a>BasicType
Задает базовый тип символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
enum BasicType {   
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
 btNoType  
 Базовый тип не указан.  
  
 btVoid  
 Базовый тип является `void`.  
  
 btChar  
 Базовый тип является `char` (тип C/C++).  
  
 btWChar  
 Базовый тип является расширенных символов (Юникод) (`WCHAR`).  
  
 btInt  
 Базовый тип является `signed int` (тип C/C++).  
  
 btUInt  
 Базовый тип является `unsigned int` (тип C/C++).  
  
 btFloat  
 Базовый тип является числом с плавающей запятой (`FLOAT`).  
  
 btBCD  
 Базовый тип является десятичным закодированных двоичный файл (`BCD`).  
  
 btBool  
 Базовый тип является логическое значение (`BOOL`).  
  
 btLong  
 Базовый тип является `long int` (тип C/C++).  
  
 btULong  
 Базовый тип является `unsigned long int` (тип C/C++).  
  
 btCurrency  
 Базовый тип — это валюта.  
  
 btDate  
 Базовый тип является даты и времени (`DATE`).  
  
 btVariant  
 Базовый тип является структурой типа переменной (`VARIANT`).  
  
 btComplex  
 Базовый тип — это комплексное число.  
  
 btBit  
 Базовый тип — бит.  
  
 btBSTR  
 Базовый тип является базовым или двоичные строки (`BSTR`).  
  
 btHresult  
 Базовый тип является `HRESULT`.  
  
## <a name="remarks"></a>Примечания  
 Возвращаемые значения в этом перечислении [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)