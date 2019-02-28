---
title: IDiaSession::symbolById | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b58fcf55741975a776e222b2845ae50774e7fc9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645515"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Получает символ по его уникальному идентификатору.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Параметры
`id`

[in] Уникальный идентификатор.

`ppSymbol`

[out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) извлечь объект, представляющий символ.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Указанный идентификатор является внутренним классом DIA SDK чтобы сделать все символы уникальным уникальное значение.

Этот метод может использоваться, например, для получения символ, представляющий тип другого символа (см. пример).

## <a name="example"></a>Пример
В этом примере извлекаются [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) представляющий от другого типа. В этом примере показано, как использовать `symbolById` метод в сеансе. Более простой подход является вызов [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) метод для извлечения типа символа напрямую.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>См. также раздел
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
