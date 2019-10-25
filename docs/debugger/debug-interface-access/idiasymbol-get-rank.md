---
title: 'IDiaSymbol:: get_rank | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cff86464a4034ad869cdfe231a88ad128dbf52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739490"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
Извлекает ранг (число измерений) многомерного массива FORTRAN.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает количество измерений в многомерном массиве FORTRAN.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Заметки
 Ранг — это число измерений в массиве, в котором массив объявлен как `myarray[1,2,3]`. Этот пример имеет ранг 3 и 3 измерения. Параметр Rank не применяется к C++ , в котором используется концепция массива массивов для каждого измерения (то есть `myarray[1][2][3]`).

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)