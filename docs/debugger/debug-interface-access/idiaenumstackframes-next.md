---
title: IDiaEnumStackFrames::Next | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9cf220c65cf11836e64a7e1f4c0142c89669f4b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833313"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Извлекает указанное число элементов кадра стека из последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 celt

[in] Число элементов кадра стека в перечислителе требуется получить.

 rgelt

[out] Массив, который должен быть заполнен с требуемым [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) объектов.

 pceltFetched

[out] Возвращает число стека элементы-фреймы в выбранных перечислитель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если больше нет кадров стека. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)