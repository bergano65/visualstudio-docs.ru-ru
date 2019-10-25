---
title: THUNK_ORDINAL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1de2d6c9700dcb7b1106c3693d855bb1d8ae2cfa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738500"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Обозначает типы преобразователей.

## <a name="syntax"></a>Синтаксис

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>Элементы
Стандартный преобразователь THUNK_ORDINAL_NOTYPE.

THUNK_ORDINAL_ADJUSTOR преобразователь `this`.

Преобразователь виртуальных вызовов THUNK_ORDINAL_VCALL.

THUNK_ORDINAL_PCODE преобразователь P-code.

Преобразователь отложенной загрузки THUNK_ORDINAL_LOAD.

THUNK_ORDINAL_TRAMP_INCREMENTAL добавочный трамполине (преобразователь трамполине используется для возврата вызовов из одного пространства памяти в другое).

Преобразователь трамполине точки ветвления THUNK_ORDINAL_TRAMP_BRANCHISLAND.

## <a name="remarks"></a>Заметки
Значения в этом перечислении возвращаются из вызова метода [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
