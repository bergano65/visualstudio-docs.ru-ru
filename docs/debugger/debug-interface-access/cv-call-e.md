---
title: CV_call_e | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5fea99994b891250dad85cfc43320848df98f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555108"
---
# <a name="cvcalle"></a>CV_call_e
Определяет соглашение вызова для функции.

> [!NOTE]
> Здесь описаны только наиболее часто встречающихся значений перечисления. В файле заголовка cvconst.h доступен полный перечисления.

## <a name="syntax"></a>Синтаксис

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>Элементы
CV_CALL_NEAR_C указывает соглашение вызова функций, с помощью практически извещающей справа налево. Вызываемая функция очищает стек.

Указывает CV_CALL_NEAR_FAST соглашение о вызове функции с помощью Push-уведомлений почти слева направо с регистрирует. Эта функция использует количеству байтов, параметр для очистки стека.

CV_CALL_NEAR_STD указывает соглашение вызова функций, с помощью практически стандартный вызов (отправка справа налево).

Указывает CV_CALL_NEAR_SYS вызовите соглашение вызова функций, с помощью практически системы.

CV_CALL_THISCALL указывает соглашение о вызове функции с помощью `this` вызова (`this` указатель передан в регистре).

Указывает CV_CALL_CLRCALL вызова функций правилом, используемым с Common Language Runtime (CLR) (также известный как управляемый код соглашение о вызовах).

## <a name="remarks"></a>Примечания
Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) метод.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
