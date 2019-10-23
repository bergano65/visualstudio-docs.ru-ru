---
title: 'IDiaSession:: Симсарикуив | Документация Майкрософт'
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
ms.openlocfilehash: 61cfc582f11670af8c956c3334681284ce5172a6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741866"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Проверяет, эквивалентны ли два символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Параметры
 `symbolA`

окне Первый объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , используемый в сравнении.

 `symbolB`

окне Второй объект `IDiaSymbol`, используемый при сравнении.

## <a name="return-value"></a>Возвращаемое значение
 Если символы эквивалентны, возвращает `S_OK`; в противном случае возвращает `S_FALSE`, символы не эквивалентны. В противном случае возвратите код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)