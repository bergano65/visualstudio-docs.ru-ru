---
title: Kind | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31be0615fd7d1da279ecf414260af21cb8239dc8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745286"
---
# <a name="datakind"></a>DataKind
Указывает конкретную область значения данных.

## <a name="syntax"></a>Синтаксис

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Элементы
Не удается определить символ данных Датаисункновн.

Элемент данных Датаислокал является локальной переменной.

Элемент данных Датаисстатиклокал является статической локальной переменной.

Элемент данных Датаиспарам является формальным параметром.

Элемент данных Датаисобжектптр является указателем объекта (`this`).

Элемент данных Датаисфилестатик является переменной с областью действия файла.

Элемент данных Датаисглобал является глобальной переменной.

Элемент данных Датаисмембер является переменной-членом объекта.

Элемент данных Датаисстатикмембер является статической переменной класса.

Элемент данных Датаисконстант является постоянным значением.

## <a name="remarks"></a>Заметки
Значения в этом перечислении возвращаются методом [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
