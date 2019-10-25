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
ms.openlocfilehash: 5deb59d4bbee06e505ba10bf1d4f08b1b06aa62d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745356"
---
# <a name="cv_call_e"></a>CV_call_e
Указывает соглашение о вызовах для функции.

> [!NOTE]
> Здесь описаны только наиболее распространенные значения перечисления. Полное перечисление доступно в файле заголовка квконст. h.

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
CV_CALL_NEAR_C указывает соглашение о вызове функции с помощью push-уведомлений NEAR слева направо. Вызывающая функция очищает стек.

CV_CALL_NEAR_FAST указывает соглашение о вызове функции с помощью push-уведомлений NEAR слева направо с регистрами. Вызываемая функция использует сумму байтов параметров для очистки стека.

CV_CALL_NEAR_STD указывает соглашение о вызове функции с использованием ближайшего стандартного вызова (push-уведомлений справа налево).

CV_CALL_NEAR_SYS указывает соглашение о вызове функции с помощью ближайшего системного вызова.

CV_CALL_THISCALL указывает соглашение о вызове функции с помощью вызова `this` (переданный в регистре `this` указатель).

CV_CALL_CLRCALL указывает соглашение о вызове функции, используемое средой CLR (также известное как соглашение о вызовах управляемого кода).

## <a name="remarks"></a>Заметки
Значения в этом перечислении возвращаются путем вызова метода [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
