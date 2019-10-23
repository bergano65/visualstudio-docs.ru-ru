---
title: Басиктипе | Документация Майкрософт
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
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745480"
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
Бтнотипе. базовый тип не задан.

Бтвоид Basic Type — это `void`.

Бтчар Basic Type — это `char` (C/C++ Type).

Бтвчар Basic Type — это широкий символ (в Юникоде) (`WCHAR`).

Тип Бтинт Basic — `signed int` (C/C++ тип).

Тип Бтуинт Basic — `unsigned int` (C/C++ тип).

Бтфлоат Basic Type — это число с плавающей запятой (`FLOAT`).

Бтбкд Basic Type — это двоично-кодированное десятичное число (`BCD`).

Базовый тип Бтбул — логическое значение (`BOOL`).

Бтлонг Basic Type — это `long int` (C/C++ Type).

Бтулонг Basic Type — это `unsigned long int` (C/C++ Type).

Базовый тип Бткурренци — Currency.

Базовый тип Бтдате — Дата и время (`DATE`).

Бтвариант Basic Type — это структура типа переменной (`VARIANT`).

Бткомплекс Basic Type — это комплексное число.

Тип Бтбит Basic является битом.

Базовый тип Бтбстр — это базовая или двоичная строка (`BSTR`).

Бсресулт Basic Type — это `HRESULT`.

## <a name="remarks"></a>Заметки
Значения в этом перечислении возвращаются методом [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
