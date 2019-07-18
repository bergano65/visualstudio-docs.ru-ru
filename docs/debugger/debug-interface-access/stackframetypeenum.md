---
title: StackFrameTypeEnum | Документация Майкрософт
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
ms.openlocfilehash: 44f715c4f74d9b120b324e2d68417a24c9b42684
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854834"
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
`FrameTypeFPO` Указатель на фреймы опустить; FPO сведения недоступны.

`FrameTypeTrap` Кадр перехвата ядра.

`FrameTypeTSS` Кадр перехвата ядра.

`FrameTypeStandard` Стандартный кадр стека EBP.

`FrameTypeFrameData` Указатель на фреймы опустить; Кадр данных сведения о доступных.

`FrameTypeUnknown` Кадр, который не поддерживает любой отладочной информации.

## <a name="remarks"></a>Примечания
Значения в этом перечислении возвращаются путем вызова [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) метод.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
