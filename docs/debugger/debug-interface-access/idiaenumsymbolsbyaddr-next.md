---
title: IDiaEnumSymbolsByAddr::Next | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e52567eddcbb6c4f372256e66b7b723bc7aa7394
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833445"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Извлекает следующий символы в порядке по адресу.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 celt

[in] Количество символов в перечислителе требуется получить.

 rgelt

[out] Массив, который должен быть заполнен с помощью [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекта, представляющие нужные символы.

 pceltFetched

[out] Возвращает количество символов в выбираемых перечислитель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` при наличии отсутствуют дополнительные символы. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод обновляет позицию перечислителя, количество выбранных элементов.

## <a name="see-also"></a>См. также
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)