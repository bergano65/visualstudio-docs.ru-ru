---
title: LocationType | Документация Майкрософт
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
ms.openlocfilehash: faff61833cb130902efbd64d60a16f74c507a3e2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627939"
---
# <a name="locationtype"></a>LocationType
Указывает тип данных о географическом положении, содержащихся в символе.

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
`LocIsNull` Сведения о расположении недоступны.

`LocIsStatic` Расположение является статическим.

`LocIsTLS` Расположение находится в локальном хранилище потока.

`LocIsRegRel` Расположение относительно регистра.

`LocIsThisRel` Расположение — `this`— относительный.

`LocIsEnregistered` Расположение — в регистре.

`LocIsBitField` Расположением является битовым полем.

`LocIsSlot` Располагается в слот промежуточного языка MSIL (Microsoft).

`LocIsIlRel` Расположение — относительно MSIL.

`LocInMetaData` Расположение находится в метаданных.

`LocIsConstant` Расположение имеет постоянное значение.

`LocTypeMax` Количество типов расположение в этом перечислении.

## <a name="remarks"></a>Примечания
Свойства, доступные для [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) интерфейс зависят от расположения символа в файле образа. Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md).

Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) метод.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также раздел
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)
