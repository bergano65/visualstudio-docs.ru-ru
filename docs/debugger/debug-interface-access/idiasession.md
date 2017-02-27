---
title: "IDiaSession | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession - интерфейс"
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IDiaSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Предоставляет контекст запроса для символов отладки.  
  
## Синтаксис  
  
```  
IDiaSession : IUnknown  
```  
  
## Методы  
 В следующей таблице показаны методы `IDiaSession`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaSession::get\_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Извлекает адрес загрузки для исполняемого файла, который соответствует символам в этом хранилище символов.  Это то же значение, которое было передано методу `put_loadAddress`.|  
|[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Задает адрес загрузки для исполняемого файла, который соответствует символам в этом хранилище символов. **Note:**  Важно вызывать этот метод при получении объект `IDiaSession` и прежде чем начать использование объекта.|  
|[IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)|Извлекает ссылку на глобальную область.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Возвращает перечислитель для всех таблиц, содержащихся в хранилище символов.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Возвращает перечислитель для всех именованных символов для статических местах.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Извлекает все дочерние элементы указанного родительского идентификатора, соответствующие имени и типа символа.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Извлекает указанный символьный тип, содержащий либо ближайший к указанный адрес.|  
|[IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)|Извлекает указанный символьный тип, содержащий либо ближайший к, заданный относительный виртуальный адрес \(RVA\).|  
|[IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)|Извлекает указанный символьный тип, содержащий либо ближайший к указанный виртуальный адрес \(VA\).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Получает символ, который содержит указанный маркер метаданных.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Проверяет наличие 2 символов эквивалентны.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Получает символ его уникальным идентификатором.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Извлекает указанный символьный тип, содержащий либо ближайший к относительный виртуальный адрес указанные и смещения.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Извлекает указанный символьный тип, содержащий либо ближайший к указанный виртуальный адрес и смещения.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Извлекает исходный файл compiland и именем.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Извлекает исходный файл идентификатором исходного файла.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Получение числа линии в указанный идентификатор compiland и исходного файла.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Извлекает линии в указанном compiland, содержащих определенный адрес.|  
|[IDiaSession::findLinesByRVA](../Topic/IDiaSession::findLinesByRVA.md)|Извлекает линии в указанном compiland, которые содержат заданный относительный виртуальный адрес.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Находит число линии для линий, содержащегося в заданном диапазоне адресов.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Извлекает линии в указанном compiland исходным файлом и номеру линии.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Извлекает источник, который был помещен в хранилище символов поставщиками атрибута или другими компонентами процесса компиляции.|  
|[IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)|Перечисляемая последовательность восстановления отладки потоки данных.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Извлекает перечисление, которое позволяет клиенту выполнять перебор всех кадров встроенного по заданному адресу.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Извлекает перечисление, которое позволяет клиенту выполнять перебор всех кадров относительному адресу встроенного по указанному виртуальному \(RVA\).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Извлекает перечисление, которое позволяет клиенту выполнять перебор всех кадров встроенного по указанному виртуальному адресу \(VA\).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Извлекает перечисление, которое позволяет клиенту выполнять перебор число линии всех функций, является встроенной, прямо или косвенно, указанным родительским символом.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Извлекает перечисление, которое позволяет клиенту выполнять перебор число линии всех функций, является встроенной, прямо или косвенно, указанным родительским символом и содержится в указанный диапазон адресов.|  
|[IDiaSession::findInlineeLinesByRVA](../Topic/IDiaSession::findInlineeLinesByRVA.md)|Извлекает перечисление, которое позволяет клиенту выполнять перебор число линии всех функций, является встроенной, прямо или косвенно, указанным родительским символом и содержится в заданный относительный виртуальный адрес \(RVA\).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Извлекает перечисление, которое позволяет клиенту выполнять перебор число линии всех функций, является встроенной, прямо или косвенно, указанным родительским символом и содержится в указанный виртуальный адрес \(VA\).|  
|[IDiaSession::findInlineeLinesByLinenum](../Topic/IDiaSession::findInlineeLinesByLinenum.md)|Извлекает перечисление, которое позволяет клиенту выполнять перебор число линии всех функций, является встроенной, прямо или косвенно, определенных в файле источника и номер линии.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Извлекает перечисление, которое позволяет клиенту выполнять перебор число линии всех встроенным функциям, которые соответствуют заданному имени.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Возвращает перечисление символов переменной, которая соответствует указанным значением тега в родительский функции заглушки сочетаний клавиш.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Если соответствующее значение тега, этот метод возвращает перечисление символов, содержащихся в заданной родительской функции заглушки сочетаний клавиш в указанном относительного виртуальному адресу.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Возвращает перечисление символов для встроенных кадров, соответствующий указанному имени встроенной функции.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Возвращает перечисление символов для встроенных кадров, соответствующие указанному расположению источников.|  
  
## Заметки  
 Важно вызвать метод [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) после создания объекта `IDiaSession` — и значение, переданное методу `put_loadAddress` должно быть ненулевым — для всех свойств виртуального адресного пространства \(VA\) символов для быть доступно.  Адрес загрузки поступает от загружаемой программы любой отлаживаемой исполняемому файлу.  Например, можно вызвать функцию Win32 `GetModuleInformation` чтобы получить адрес загрузки для исполняемого файла, заданный дескриптор к исполняемому файлу.  
  
## Пример  
 В этом примере показано, как получить интерфейс `IDiaSession` как часть общей инициализации пакета SDK для доступа к интерфейсу отладки.  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Запрос PDB\-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)