---
title: IDiaSymbol::get_baseType | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2844003bf7ec81b256537fe06520dfdff473faa
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227281"
---
# <a name="idiasymbolgetbasetype"></a>IDiaSymbol::get_baseType
Возвращает базовый тип для этого символа<em>.</em>

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
`pRetVal`  
[out] Возвращает значение из [перечисление BasicType](../../debugger/debug-interface-access/basictype.md) перечисление, определяющее, базовый тип символа.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
Базовый тип для символа может определяться, сначала Получив тип символа и затем опроса, возвращаемый тип для базового типа. Обратите внимание, что некоторые символы не могут иметь базовый тип, например, имя структуры.

## <a name="example"></a>Пример

```C++
IDiaSymbol* pType;
CComPtr<IDiaSymbol> pBaseType;
if (pType->get_type( &pBaseType ) == S_OK)
{
    BasicType btBaseType;
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)
    {
        // Do something with basic type.
    }
}
```

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 7.0|

## <a name="see-also"></a>См. также раздел
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
[Перечисление BasicType](../../debugger/debug-interface-access/basictype.md)  
[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
