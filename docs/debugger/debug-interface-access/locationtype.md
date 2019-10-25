---
title: Локатионтипе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738638"
---
# <a name="locationtype"></a>LocationType
Указывает тип сведений о расположении, содержащихся в символе.

## <a name="syntax"></a>Синтаксис

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>Элементы
сведения о расположении `LocIsNull` недоступны.

Расположение `LocIsStatic` является статическим.

Расположение `LocIsTLS` находится в локальном хранилище потока.

Расположение `LocIsRegRel` является относительным для регистра.

`LocIsThisRel` расположение относительно `this`.

Расположение `LocIsEnregistered` находится в регистре.

Расположение `LocIsBitField` находится в битовом поле.

`LocIsSlot` расположение — это слот MSIL.

`LocIsIlRel` расположение относительно MSIL.

Расположение `LocInMetaData` находится в метаданных.

Расположение `LocIsConstant` находится в постоянном значении.

`LocTypeMax` число типов расположения в этом перечислении.

## <a name="remarks"></a>Заметки
Свойства, доступные для интерфейса [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , зависят от расположения символа в файле изображения. Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md).

Значения в этом перечислении возвращаются путем вызова метода [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)
