---
title: Запрос. PDB-файл | Документация Майкрософт
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
ms.openlocfilehash: dcc97fc6c508a47088cb2e96c9132c88c8fcb75c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996818"
---
# <a name="querying-the-pdb-file"></a>Запрос PDB-файла
Файл базы данных программы (с расширением PDB) — это двоичный файл, который содержит тип и символьную отладочную информацию, собранные в ходе компиляции и компоновки проекта. PDB-файл создается при компиляции программы C/C++ с **/ZI** или **/ZI** или [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], или [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] программировать **/debug** параметр. Объектные файлы содержат ссылки в PDB-файла для отладочной информации. Дополнительные сведения о PDB-файлы, см. в разделе [PDB-файлы](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Приложения доступа к интерфейсу отладки можно использовать следующие общие действия для получения сведений о различных символов, объекты и элементы данных в исполняемый образ.  
  
### <a name="to-query-the-pdb-file"></a>Запрос PDB-файла  
  
1.  Получения источника данных путем создания [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) интерфейс.  
  
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
  
2.  Вызовите [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) или [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) загрузить отладочную информацию.  
  
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
  
3.  Вызовите [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) открыть [IDiaSession](../../debugger/debug-interface-access/idiasession.md) для получения доступа к отладочной информации.  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Используйте методы в `IDiaSession` запрос для символов в источнике данных.  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Используйте `IDiaEnum*` интерфейсы для перечисления и просмотра символы или другие элементы отладочную информацию.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)