---
title: IDiaSymbol::get_code | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_code method
ms.assetid: 5f425fa3-7ba6-4979-8b3e-0fcd06cbba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4616751a6d0e78a1d27afb1e3553109cd82d3ec7
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64793931"
---
# <a name="idiasymbolgetcode"></a>IDiaSymbol::get_code
Получает флаг, указывающий, относится ли символ к адрес кода.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_code ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если символ относится к адрес кода, в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 7.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)