---
title: Диааддрессмапентри | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745262"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Описывает запись в карте адресов.

## <a name="syntax"></a>Синтаксис

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Элементы
`rva` относительный виртуальный адрес (RVA) в образе A.

`rvaTo` относительный виртуальный адрес, `rva` сопоставляется в образе б.

## <a name="remarks"></a>Заметки
Таблица адресов обеспечивает перевод из одного макета изображения (A) в другой (B). Массив структур `DiaAddressMapEntry`, упорядоченный по `rva` определяет карту адресов.

Чтобы преобразовать адрес, `addrA` в Image A в адрес `addrB` в образе б выполните следующие действия.

1. Выполните поиск по карте для записи `e` с самым большим `rva` меньше или равно `addrA`.

2. Задайте `delta = addrA - e.rva`.

3. Задайте `addrB = e.rvaTo + delta`.

    Массив структур `DiaAddressMapEntry` передается методу [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>Требования
Заголовок: dia2. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
