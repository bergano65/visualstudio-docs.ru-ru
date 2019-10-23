---
title: 'IDiaSession:: Симболбид | Документация Майкрософт'
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
ms.openlocfilehash: b0ffcb6c438150bff82f17a66c3347c300b17d72
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741882"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Извлекает символ по его уникальному идентификатору.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Параметры
`id`

окне Уникальный идентификатор.

`ppSymbol`

заполняет Возвращает объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий полученный символ.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
Указанный идентификатор — это уникальное значение, которое внутренне используется пакетом SDK для DIA, чтобы сделать все символы уникальными.

Этот метод можно использовать, например, для получения символа, представляющего тип другого символа (см. пример).

## <a name="example"></a>Пример
В этом примере извлекается [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий тип другого символа. В этом примере показано, как использовать метод `symbolById` в сеансе. Более простой подход заключается в вызове метода [IDiaSymbol:: get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) для непосредственного получения символа типа.

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

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
