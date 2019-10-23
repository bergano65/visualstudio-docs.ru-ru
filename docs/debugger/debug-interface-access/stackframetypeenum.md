---
title: Стаккфраметипинум | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b0c9dd106e5744a369ddaa6cb870788f7464d3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738554"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Указывает тип кадра стека.

## <a name="syntax"></a>Синтаксис

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>Элементы
`FrameTypeFPO` указатель фрейма опущен; Сведения о FPO доступны.

`FrameTypeTrap` кадре ловушки ядра.

`FrameTypeTSS` кадре ловушки ядра.

Стандартный кадр стека EBP `FrameTypeStandard`

`FrameTypeFrameData` указатель фрейма опущен; Сведения о данных кадра доступны.

`FrameTypeUnknown` кадр, у которого нет отладочной информации.

## <a name="remarks"></a>Заметки
Значения в этом перечислении возвращаются путем вызова метода [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
