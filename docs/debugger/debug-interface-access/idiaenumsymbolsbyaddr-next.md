---
title: 'Идиаенумсимболсбяддр:: Next | Документация Майкрософт'
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
ms.openlocfilehash: 424924f3fab62cf862420d58c947bba16343141d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743883"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Извлекает следующие символы в упорядочении по адресу.

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

окне Число извлекаемых символов в перечислителе.

 rgelt

заполняет Массив, который должен быть заполнен объектом [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющим нужные символы.

 pceltFetched

заполняет Возвращает количество символов в полученном перечислителе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если больше нет символов. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Заметки
 Этот метод обновляет расположение перечислителя по количеству извлекаемых элементов.

## <a name="see-also"></a>См. также
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)