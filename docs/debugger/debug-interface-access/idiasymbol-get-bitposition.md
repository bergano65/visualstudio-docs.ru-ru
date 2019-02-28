---
title: IDiaSymbol::get_bitPosition | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_bitPosition method
ms.assetid: b0059407-8655-497b-81ca-025595989371
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 521a21b2d3534433fe72ea6bd9578c0e668755ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611851"
---
# <a name="idiasymbolgetbitposition"></a>IDiaSymbol::get_bitPosition
Получает положение разряда расположение. Используется, когда [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) является `LocIsBitField`.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_bitPosition ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает положение разряда расположения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 7.0|

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)