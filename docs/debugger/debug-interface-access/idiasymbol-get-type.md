---
title: IDiaSymbol::get_type | Документация Майкрософт
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
ms.openlocfilehash: 4fa57b1f289f9cc5e8c57c08b6d51bb1677c3db4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608257"
---
# <a name="idiasymbolgettype"></a>IDiaSymbol::get_type
Возвращает символ, представляющий тип для этого символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Параметры
`pRetVal`

[out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий тип этого символа.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
Чтобы определить тип символа, необходимо вызвать этот метод и просмотрите полученный в результате [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекта. Обратите внимание на то, что существует возможность символ, не относится к типу. Например, имя структуры не имеет типа, но он может иметь дочерние символы (использовать [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md) метод для проверки этих дочерних действий).

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

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
