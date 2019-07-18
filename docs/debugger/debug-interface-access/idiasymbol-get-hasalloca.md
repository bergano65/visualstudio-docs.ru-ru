---
title: IDiaSymbol::get_hasAlloca | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAlloca method
ms.assetid: 3b9fb747-670b-4da7-bb70-612f7b911786
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 457f446af4a91141962fbbd3055d9ce4980c719a
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64808787"
---
# <a name="idiasymbolgethasalloca"></a>IDiaSymbol::get_hasAlloca
Получает флаг, указывающий, содержит ли функция вызов `alloca` (который используется для выделения памяти в стеке).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT get_hasAlloca(   BOOL *pFlag);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

[out] Возвращает `TRUE` Если функция содержит вызов `alloca`; в противном случае возвращает `FALSE`.

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