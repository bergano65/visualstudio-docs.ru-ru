---
title: IDiaSymbol::get_numberOfColumns | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 64834351-e2c9-4f1c-9dc0-2abb5478bc63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49482c99f3d735618cb9caab02a04fea1e81ebc9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622323"
---
# <a name="idiasymbolgetnumberofcolumns"></a>IDiaSymbol::get_numberOfColumns
Возвращает число столбцов в матрице.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_numberOfColumns(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Указатель на `DWORD` , содержащий число столбцов в матрице.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)