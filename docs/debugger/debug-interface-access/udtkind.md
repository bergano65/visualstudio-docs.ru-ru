---
title: UdtKind | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 511beae100529f0db555eca0a8ddb995d7a335d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62853514"
---
# <a name="udtkind"></a>UdtKind
Описывает различные определяемого пользователем типа (UDT).

## <a name="syntax"></a>Синтаксис

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>Элементы
UdtStruct определяемого пользователем ТИПА — это структура.

UdtClass определяемого пользователем ТИПА — это класс.

UdtUnion определяемого пользователем ТИПА — это объединение.

UdtInterface определяемый пользователем тип является интерфейсом.

## <a name="remarks"></a>Примечания
Возвращаемые значения в этом перечислении [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) метод.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
