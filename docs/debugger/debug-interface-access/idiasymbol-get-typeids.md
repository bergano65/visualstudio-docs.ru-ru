---
title: IDiaSymbol::get_typeIds | Документация Майкрософт
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
ms.openlocfilehash: 12024a3a024f2c9433e144790c0a513d4e33df12
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643747"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Извлекает массив значений типа специфичные для компилятора идентификатор для этого символа.

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

[in] Размер буфера для хранения данных.

 `pcTypeIds`

[out] Возвращает количество `typeIds` записаны, или, если `typeIds` является `NULL`, затем общее число доступных идентификаторов типов.

 `typeIds[]`

[out] Массив, заполненный идентификаторы типа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)