---
title: DataKind | Документация Майкрософт
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
ms.openlocfilehash: bf8e59bf79355b4e610091ac8662b8d2a01af322
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318684"
---
# <a name="datakind"></a>DataKind
Указывает область конкретного значения данных.

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
DataIsUnknown  
Не удается определить символ данных.

DataIsLocal  
Элемент данных — это локальная переменная.

DataIsStaticLocal  
Элемент данных является статической локальной переменной.

DataIsParam  
Элемент данных является формальным параметром.

DataIsObjectPtr  
Элемент данных является указателем объекта (`this`).

DataIsFileStatic  
Элемент данных — это переменная уровня файла.

DataIsGlobal  
Элемент данных является глобальной переменной.

DataIsMember  
Элемент данных является переменной члена объекта.

DataIsStaticMember  
Элемент данных является статической переменной класса.

DataIsConstant  
Элемент данных — это постоянное значение.

## <a name="remarks"></a>Примечания
Возвращаемые значения в этом перечислении [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) метод.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также раздел
[Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
