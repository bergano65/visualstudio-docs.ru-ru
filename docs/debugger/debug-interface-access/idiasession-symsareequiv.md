---
title: IDiaSession::symsAreEquiv | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0253104cf29e86825fadc8c8bd18133e0d3cf593
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839079"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Проверяет, являются ли эквивалентными двух символов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Параметры
 `symbolA`

[in] Первый [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, используемый для сравнения.

 `symbolB`

[in] Второй `IDiaSymbol` объект, используемый для сравнения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение, если символы эквивалентны, `S_OK`; в противном случае возвращает `S_FALSE`, символы не эквивалентны. В противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)