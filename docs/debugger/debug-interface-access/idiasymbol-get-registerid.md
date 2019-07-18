---
title: IDiaSymbol::get_registerId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e2b1cbb6837ca139e735bef17bc0c2712d9cae7
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786585"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Извлекает обозначение register расположения при [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) присваивается `LocIsEnregistered`.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает обозначение register расположения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Если символ является относительно регистр, то есть если символа [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) присваивается `LocIsRegRel`, использовать `get_registerId` метод, а затем с помощью вызова [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) метод для получения смещения из реестра, где находится символ.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)