---
title: Запрос к. PDB-файл | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b9013d41ac4d5ca890e7cc9e09b5eb9415cb640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691332"
---
# <a name="querying-the-pdb-file"></a>Запрос PDB-файла
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Файл базы данных программы (Extension. pdb) представляет собой двоичный файл, содержащий тип и символьную отладочную информацию, собранную в ходе компиляции и связывания проекта. PDB-файл создается при компиляции программы C/C++ с **/Zi** или **/Zi** либо с [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] параметром **/Debug** , или с помощью программы. Объектные файлы содержат ссылки на PDB-файл для отладки данных. Дополнительные сведения о PDB-файлах см. в разделе [PDB-файлы](https://msdn.microsoft.com/1761c84e-8c2c-4632-9649-b5f99964ed3f). Приложение DIA может использовать следующие общие шаги для получения сведений о различных символах, объектах и элементах данных в исполняемом образе.  
  
### <a name="to-query-the-pdb-file"></a>Запрос к PDB-файлу  
  
1. Получение источника данных путем создания интерфейса [идиадатасаурце](../../debugger/debug-interface-access/idiadatasource.md) .  
  
    ```cpp#  
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
  
    ```cpp#  
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
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4. Используйте методы в `IDiaSession` для запроса символов в источнике данных.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5. Используйте `IDiaEnum*` интерфейсы для перечисления и просмотра символов или других элементов отладочной информации.  
  
    ```cpp#  
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
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
