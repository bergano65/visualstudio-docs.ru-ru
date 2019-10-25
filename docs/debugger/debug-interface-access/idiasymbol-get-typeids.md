---
title: 'IDiaSymbol:: get_typeIds | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4db7c1d7e3ed19268d94b28a7f0500788f7d21f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739071"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Извлекает массив значений идентификаторов типов, относящихся к компилятору, для этого символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Параметры
 `cTypeIds`

окне Размер буфера для хранения данных.

 `pcTypeIds`

заполняет Возвращает число записанных `typeIds` или, если `typeIds` `NULL`, то общее число доступных идентификаторов типов.

 `typeIds[]`

заполняет Массив, который должен быть заполнен идентификаторами типов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)