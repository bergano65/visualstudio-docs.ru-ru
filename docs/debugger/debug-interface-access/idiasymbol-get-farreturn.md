---
title: IDiaSymbol::get_farReturn | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_farReturn method
ms.assetid: 141df0e9-f4d9-4330-a043-5d9ea865257f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 209ce1189963a3943a691b71c840474c3da1a07c
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64808829"
---
# <a name="idiasymbolgetfarreturn"></a>IDiaSymbol::get_farReturn
Получает флаг, указывающий, содержит ли далеко возвращаемого значения функции.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_farReturn(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

[in] Возвращает `TRUE` Если эта функция использует гораздо возвращаемого значения, в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 8.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)