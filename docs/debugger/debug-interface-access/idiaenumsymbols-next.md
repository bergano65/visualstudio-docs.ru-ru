---
title: IDiaEnumSymbols::Next | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Next method
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef151b369c18863b8a87944cdbf69fed9aeb0840
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833393"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
Извлекает указанное число символов в последовательности перечисления.

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

[out] Массив, который должен быть заполнен с помощью [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекты, представляющие нужные символы.

 pceltFetched

[out] Возвращает количество символов в выбираемых перечислитель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` при наличии отсутствуют дополнительные символы. В противном случае возвращается код ошибки.

## <a name="example"></a>Пример

```C++
IDiaEnumSymbols* pEnum
CComPtr< IDiaSymbol> pSym;
DWORD celt;
pEnum->Next( 1, &pSym, &celt );
```

## <a name="see-also"></a>См. также
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)