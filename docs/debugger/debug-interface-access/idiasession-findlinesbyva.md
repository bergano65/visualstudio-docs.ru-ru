---
title: IDiaSession::findLinesByVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2503707b8fd5907cd028b7af3e67cd5acd76a00
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227791"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Извлекает информация о номере строки для строк, содержащихся в указанный диапазон виртуальных адресов (VA).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Параметры
`va`  
[in] Указывает адрес как ва.

`length`  
[in] Указывает число байтов из диапазона адресов, чтобы охватить с этим запросом.

`ppResult`  
[out] Возвращает [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , содержащий список всех строке номера, охватывают указанный диапазон адресов.

## <a name="example"></a>Пример
В этом примере показана функция, получающий все номера строк, содержащихся в функции, используя функции виртуальный адрес и длину.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>См. также раздел
[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
[IDiaSession](../../debugger/debug-interface-access/idiasession.md)
