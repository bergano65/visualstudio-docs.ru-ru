---
title: IDiaSymbol::get_types | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f99530e790594e6966611b97a3d9a2c0a0cc04d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602706"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Извлекает массив типов специфичные для компилятора для этого символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Параметры
 `cTypes`

[in] Размер буфера для хранения данных.

 `pcTypes`

[out] Возвращает количество типов, созданных, или, если `types` параметр `NULL`, то общее число доступных типов.

 `types[]`

[out] Массив, который должен быть заполнен с помощью [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекты, представляющие все типы для этого символа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)