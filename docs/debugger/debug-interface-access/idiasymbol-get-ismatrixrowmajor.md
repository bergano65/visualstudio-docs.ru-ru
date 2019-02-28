---
title: IDiaSymbol::get_isMatrixRowMajor | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 146ef53f8a5d893e394834c7d5702c8992fdd20a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611013"
---
# <a name="idiasymbolgetismatrixrowmajor"></a>IDiaSymbol::get_isMatrixRowMajor
Указывает, является ли матрица основной строки.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_isMatrixRowMajor(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Указатель на `BOOL` , указывающий, является ли матрица основной строки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)