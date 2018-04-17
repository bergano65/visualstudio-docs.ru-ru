---
title: IDiaSession | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06c401fd1c0b2e65e320e9d63150eba322f06f23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasession"></a>IDiaSession
Предоставляет контекст запроса для отладочных символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDiaSession`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Извлекает адрес загрузки для исполняемого файла, соответствующее символов в данном хранилище символов. Это то же значение, которое было передано `put_loadAddress` метод.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Задает адрес загрузки для исполняемого файла, соответствующее для символов в данном хранилище символов. **Примечание:** необходимо вызвать этот метод при получении `IDiaSession` объекта и перед началом работы с помощью объекта.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Извлекает ссылку на глобальную область.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Возвращает перечислитель для всех таблиц, содержащихся в хранилище символов.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Возвращает перечислитель для всех именованных символов в статических расположениях.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Извлекает все дочерние элементы идентификатора указанного родительского объекта, соответствующие типу наименование и символ.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Возвращает тип указанного символа, который содержит или близок к указанному адресу.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Возвращает тип указанного символа, который содержит или ближайший к указанной относительный виртуальный адрес (RVA).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Возвращает тип указанного символа, который содержит или близок к указанному виртуальному адресу (VA).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Возвращает символ, который содержит указанный токен метаданных.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Проверяет, являются ли эквивалентными двух символов.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Возвращает символ, его уникальный идентификатор.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Возвращает тип указанного символа, который содержит или ближайший к указанной относительный виртуальный адрес и смещение.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Возвращает тип указанного символа, который содержит или близок к указанному виртуальному адресу и смещение.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Извлекает компилируемого объекта и имя исходного файла.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Извлекает исходный файл, идентификатор исходного файла.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Возвращает номера строк в указанной компилируемого объекта и исходный идентификатор файла.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Извлекает строк в указанной компилируемого объекта, которые содержат указанный адрес.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Извлекает строк в указанной компилируемого объекта, которые содержат указанный относительный виртуальный адрес.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Находит сведения о номерах строк для строк, содержащихся в указанный диапазон адресов.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Извлекает строки в указанной компилируемого объекта с исходного файла и номер строки.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Получает источник, который был помещен в хранилище символов поставщиками атрибута или другие компоненты в процессе компиляции.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Возвращает перечислимый последовательности отладки потоков данных.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Возвращает перечисление, которое позволяет клиенту проходить через все фреймы для данного адреса.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Возвращает перечисление, которое позволяет клиенту проходить через все фреймы для указанного относительного виртуального адреса (RVA).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Возвращает перечисление, которое позволяет клиенту проходить через все встроенные рамки указанного виртуального адреса (VA).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Возвращает перечисление, которое позволяет клиенту итерации сведения о номерах строк для всех функций, которые являются встроенными, напрямую или косвенно, символ из указанного родительского объекта.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Возвращает перечисление, которое позволяет клиенту итерации сведения о номерах строк для всех функций, которые являются встроенными, напрямую или косвенно, символ из указанного родительского объекта и содержащихся в указанный диапазон адресов.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Возвращает перечисление, которое позволяет клиенту итерации сведения о номерах строк для всех функций, которые являются встроенными, напрямую или косвенно, символ из указанного родительского объекта и находятся в пределах указанного относительного виртуального адреса (RVA).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Возвращает перечисление, которое позволяет клиенту итерации сведения о номерах строк для всех функций, которые являются встроенными, напрямую или косвенно, символ из указанного родительского объекта и содержащихся в указанный виртуальный адрес (VA).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Возвращает перечисление, которое позволяет клиенту итерации сведения о номерах строк для всех функций, которые являются встроенными, прямо или косвенно, в указанный исходный файл и номер строки.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Возвращает перечисление, которое позволяет клиенту итерации сведения о номерах строк для всех встроенных функций, которые соответствуют заданному имени.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Возвращает перечисление символов для переменной, которая соответствует указанным значением тега в родительском объекте функция заглушки сочетаний клавиш.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Задано значение соответствующего тега, этот метод возвращает перечисление символов, содержащихся в функции заглушки сочетаний клавиш указанного родительского объекта в указанный относительный виртуальный адрес.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Возвращает перечисление символы для встроенные рамки, соответствующий имени заданной встроенной функции.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Возвращает перечисление символы для встроенного кадров, которые соответствуют указанным исходным расположением.|  
  
## <a name="remarks"></a>Примечания  
 Очень важно вызвать [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) метод после создания `IDiaSession` объект — и значение, передаваемое `put_loadAddress` метод должен иметь ненулевое значение — свойствами виртуального адреса (VA) должны быть символы возможен доступ. Адрес загрузки поступает из любой программы загружен отлаживаемому исполняемому файлу. Например, можно вызвать функцию Win32 `GetModuleInformation` для получения адреса загрузки исполняемого файла, заданный дескриптор к исполняемому файлу.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить `IDiaSession` интерфейс как часть общего инициализации пакета SDK для доступа к интерфейсу отладки.  
  
```C++  
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
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [EXE-файла](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)