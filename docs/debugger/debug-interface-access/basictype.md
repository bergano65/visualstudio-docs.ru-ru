---
title: BasicType | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03e82a8c17b33aa085b4ed64b9ba609bee183e1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829736"
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
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Элементы
btNoType, базовый тип не указан.

btVoid базовый тип является `void`.

btChar базовый тип является `char` (C /C++ типа).

btWChar базовый тип представляет собой расширенный символ (Юникод) (`WCHAR`).

btInt базовый тип является `signed int` (C /C++ типа).

btUInt базовый тип является `unsigned int` (C /C++ типа).

btFloat базовый тип является числом с плавающей запятой (`FLOAT`).

btBCD базовый тип — это десятичное число закодированных двоичный файл (`BCD`).

btBool базовый тип является логическое значение (`BOOL`).

btLong базовый тип является `long int` (C /C++ типа).

btULong базовый тип является `unsigned long int` (C /C++ типа).

btCurrency базовый тип является currency.

btDate базовый тип является даты и времени (`DATE`).

btVariant базовый тип является структурой типа переменной (`VARIANT`).

btComplex базовый тип — это комплексное число.

Базовый тип btBit немного.

btBSTR базовый тип является строкой основные или binary (`BSTR`).

btHresult базовый тип является `HRESULT`.

## <a name="remarks"></a>Примечания
Возвращаемые значения в этом перечислении [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) метод.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
