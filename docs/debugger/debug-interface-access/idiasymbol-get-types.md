---
title: 'IDiaSymbol:: get_types | Документация Майкрософт'
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
ms.openlocfilehash: 6d23ea3c4d885b3f7575c998999814d0808d03bc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739058"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
Извлекает массив типов, зависящих от компилятора, для этого символа.

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

окне Размер буфера для хранения данных.

 `pcTypes`

заполняет Возвращает число записанных типов, или, если параметр `types` имеет значение `NULL`, то общее число доступных типов.

 `types[]`

заполняет Массив, который должен быть заполнен объектами [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , которые представляют все типы для этого символа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)