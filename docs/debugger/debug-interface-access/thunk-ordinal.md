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
ms.openlocfilehash: 776ee35e57b62463d47fc6f7fa26133f507f16f9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613275"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Определяет преобразователь типов.

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
Стандартный THUNK_ORDINAL_NOTYPE преобразователь.

Объект THUNK_ORDINAL_ADJUSTOR `this` корректором преобразователь.

Преобразователь THUNK_ORDINAL_VCALL виртуального вызова.

Преобразователь THUNK_ORDINAL_PCODE P-code.

Преобразователь THUNK_ORDINAL_LOAD задержки загрузки.

Добавочные THUNK_ORDINAL_TRAMP_INCREMENTAL trampoline преобразователь (trampoline преобразователь используется для переброса вызовы из пространства памяти в другой).

Преобразователь trampoline точки THUNK_ORDINAL_TRAMP_BRANCHISLAND ветви.

## <a name="remarks"></a>Примечания
Значения в этом перечислении возвращаются из вызова [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) метод.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также раздел
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
