---
title: 'IDiaSession:: Финдлинесбива | Документация Майкрософт'
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
ms.openlocfilehash: 2513825fd2b6f4e6035f9f23295f0c9f00385d0a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742076"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Получает сведения о номере строки для строк, содержащихся в указанном диапазоне виртуальных адресов (ва).

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

окне Указывает адрес в виде ва.

`length`

окне Указывает число байтов диапазона адресов, которое будет охватывать этот запрос.

`ppResult`

заполняет Возвращает объект [идиаенумлиненумберс](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , содержащий список всех номеров строк, охватывающих указанный диапазон адресов.

## <a name="example"></a>Пример
В этом примере показана функция, которая получает все номера строк, содержащиеся в функции, с использованием виртуального адреса и длины функции.

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

## <a name="see-also"></a>См. также
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
