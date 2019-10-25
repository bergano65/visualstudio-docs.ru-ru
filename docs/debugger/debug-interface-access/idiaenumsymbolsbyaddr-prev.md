---
title: Идиаенумсимболсбяддр::P версия | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70265976e5c6e7c2b3f536f2b8648aaba44df528
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743857"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Извлекает предыдущие символы в упорядочении по адресу.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Prev ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 celt

окне Число извлекаемых символов в перечислителе.

 rgelt

заполняет Массив, который должен быть заполнен объектами [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющими нужные символы.

 pceltFetched

заполняет Возвращает количество символов в полученном перечислителе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если нет предыдущих символов. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Заметки
 Этот метод обновляет расположение перечислителя по количеству извлекаемых элементов.

## <a name="see-also"></a>См. также
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)