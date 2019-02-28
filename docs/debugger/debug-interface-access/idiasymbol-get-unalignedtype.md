---
title: IDiaSymbol::get_unalignedType | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unalignedType method
ms.assetid: fdcb38fb-490e-4d15-b4e5-3770043a366c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af79f4074d3eb7e370d3e4fb24984e70ed2d962a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606229"
---
# <a name="idiasymbolgetunalignedtype"></a>IDiaSymbol::get_unalignedType
Получает флаг, указывающий адрес не выровнен ли определяемый пользователем тип.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_unalignedType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` при невыровненных; в противном случае тип пользовательских данных возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)