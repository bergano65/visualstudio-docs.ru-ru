---
title: IDiaSymbol::get_baseSymbolId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cd504d2b-194f-4106-8de5-2de827a79cbd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8880d207a41418e12cab4374578fea4f3c4f338c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622453"
---
# <a name="idiasymbolgetbasesymbolid"></a>IDiaSymbol::get_baseSymbolId
Извлекает идентификатор символа, из которого основан указатель.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_baseSymbolId(
   DWORD *pRetVal);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Указатель на `DWORD` , содержащий идентификатор символа, из которого основан указатель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)