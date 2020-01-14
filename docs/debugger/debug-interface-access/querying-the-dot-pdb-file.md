---
title: Запрос к. PDB-файл | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a22bc8fbe65795a3c5162607a12690081e565666
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917108"
---
# <a name="querying-the-pdb-file"></a>Запрос PDB-файла
Файл базы данных программы (Extension. pdb) представляет собой двоичный файл, содержащий тип и символьную отладочную информацию, собранную в ходе компиляции и связывания проекта. PDB-C++ файл создается при компиляции C/Program с **/Zi** или **/Zi** либо [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]или программы [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] с параметром **/Debug** . Объектные файлы содержат ссылки на PDB-файл для отладки данных. Дополнительные сведения о PDB-файлах см. в разделе [PDB-файлы](/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Приложение DIA может использовать следующие общие шаги для получения сведений о различных символах, объектах и элементах данных в исполняемом образе.

### <a name="to-query-the-pdb-file"></a>Запрос к PDB-файлу

1. Получение источника данных путем создания интерфейса [идиадатасаурце](../../debugger/debug-interface-access/idiadatasource.md) .

    ```C++
    CComPtr<IDiaDataSource> pSource;
    hr = CoCreateInstance( CLSID_DiaSource,
                           NULL,
                           CLSCTX_INPROC_SERVER,
                           __uuidof( IDiaDataSource ),
                          (void **) &pSource);

    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    ```

2. Вызовите [идиадатасаурце:: лоаддатафромпдб](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) или [Идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) , чтобы загрузить отладочную информацию.

    ```C++
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    ```

3. Вызовите [идиадатасаурце:: опенсессион](../../debugger/debug-interface-access/idiadatasource-opensession.md) , чтобы открыть [IDiaSession](../../debugger/debug-interface-access/idiasession.md) , чтобы получить доступ к отладочной информации.

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. Используйте методы в `IDiaSession` для запроса символов в источнике данных.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. Используйте `IDiaEnum*` интерфейсы для перечисления и просмотра символов или других элементов отладочной информации.

    ```C++
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )
    {
        // Do something with each IDiaTable.
    }
    ```

## <a name="see-also"></a>См. также:
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
