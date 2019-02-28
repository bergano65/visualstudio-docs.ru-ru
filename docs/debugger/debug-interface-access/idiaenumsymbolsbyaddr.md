---
title: IDiaEnumSymbolsByAddr | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96ed66156fae24e22c549fffb6eb982a45e7e3f5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623077"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
Перечисляет по адресу различных символов, содержащихся в источнике данных.

## <a name="syntax"></a>Синтаксис

```
IDiaEnumSymbolsByAddr : IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDiaEnumSymbolsByAddr`.

|Метод|Описание|
|------------|-----------------|
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|Помещает перечислитель, выполняя поиск раздела и смещение.|
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|Помещает перечислитель, выполняя поиск по относительный виртуальный адрес (RVA).|
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|Помещает перечислитель, выполняя поиск по виртуальный адрес (VA).|
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Извлекает следующий символы в порядке по адресу. Обновляет позицию перечислителя число выбранных элементов.|
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Извлекает предыдущий символы в порядке по адресу. Обновляет позицию перечислителя число выбранных элементов.|
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Создает копию объекта.|

## <a name="remarks"></a>Примечания
Этот интерфейс предоставляет символы, сгруппированными по адресам. Для работы с символами, сгруппированных по типам, например `SymTagUDT` (определяемый пользователем тип) или `SymTagBaseClass`, использовать [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
Получить этот интерфейс, вызвав [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) метод.

## <a name="example"></a>Пример
Эта функция отображает имя и адрес, упорядоченный по относительному виртуальному адресу всех символов.

```C++
void ShowSymbolsByAddress(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )
    {
        Fatal( "getSymbolsByAddr" );
    }
    CComPtr<IDiaSymbol> pSym;
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )
    {
        Fatal( "symbolByAddr" );
    }
    DWORD rvaLast = 0;
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )
    {
        pSym = 0;
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )
        {
            Fatal( "symbolByAddr" );
        }
        printf( "Symbols in order\n" );
        do
        {
            CDiaBSTR name;
            if ( pSym->get_name( &name ) != S_OK )
            {
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );
            }
            else
            {
                printf( "\t0x%08X %ws\n", rvaLast, name );
            }
            pSym = 0;
            celt = 0;
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )
            {
                break;
            }
        } while ( celt == 1 );
    }
}
```

## <a name="requirements"></a>Требования
Заголовок: Dia2.h

Библиотека: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
