---
title: 'IDiaSymbol:: get_type | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60f9b9fd91535cc16b96da530db8ab43c4eaabf2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739093"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
Извлекает символ, представляющий тип для этого символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Параметры
`pRetVal`

заполняет Возвращает объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий тип этого символа.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Заметки
Чтобы определить тип символа, необходимо вызвать этот метод и проверить полученный объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Обратите внимание, что символ может не иметь типа. Например, имя структуры не имеет типа, но может иметь дочерние символы (для проверки этих дочерних элементов используется метод [IDiaSymbol:: финдчилдрен](../../debugger/debug-interface-access/idiasymbol-findchildren.md) ).

## <a name="example"></a>Пример

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
