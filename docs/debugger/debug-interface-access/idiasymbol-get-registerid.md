---
title: 'IDiaSymbol:: get_registerId | Документация Майкрософт'
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
ms.openlocfilehash: 6ffd349b56c4292de04d5d7a38e82eeafed6775e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739464"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Получает обозначение регистра расположения, если [перечисление локатионтипе](../../debugger/debug-interface-access/locationtype.md) имеет значение `LocIsEnregistered`.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает обозначение регистра расположения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Заметки
 Если символ является относительным по отношению к регистру, то есть если [перечисление локатионтипе](../../debugger/debug-interface-access/locationtype.md) символа имеет значение `LocIsRegRel`, используйте метод `get_registerId`, а затем вызов метода [IDiaSymbol:: get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) , чтобы получить смещение от регистра, в котором символ размещен.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)