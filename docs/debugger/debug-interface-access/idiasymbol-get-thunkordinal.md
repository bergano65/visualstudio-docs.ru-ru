---
title: 'IDiaSymbol:: get_thunkOrdinal | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bc8c523886d694ea413dedcf9a28e53e361882b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739141"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Возвращает тип преобразователя для функции.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает значение из перечисления [перечисления THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) , которое указывает тип преобразователя для функции.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Заметки
 Это свойство допустимо только в том случае, если символ является значением [перечисления симтаженум](../../debugger/debug-interface-access/symtagenum.md) `SymTagThunk`.

 "Преобразователь" — это фрагмент кода, который преобразует между 32-разрядным адресным пространством (также называемым плоским адресным пространством) и 16-битным адресным пространством (называемым сегментированным адресным пространством).

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)