---
title: IDiaSession | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 002e7198210e123fc2461f712bb8db442b9f25c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190719"
---
# <a name="idiasession"></a>IDiaSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Предоставляет контекст запроса для отладочных символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDiaSession` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Извлекает адрес загрузки для исполняемого файла, который соответствует символам в этом хранилище символов. Это то же значение, которое было передано в `put_loadAddress` метод.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Задает адрес загрузки для исполняемого файла, который соответствует символам в этом хранилище символов. **Примечание.**  Важно вызывать этот метод при получении `IDiaSession` объекта и перед началом использования объекта.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Извлекает ссылку на глобальную область.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Извлекает перечислитель для всех таблиц, содержащихся в хранилище символов.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Извлекает перечислитель для всех именованных символов в статических расположениях.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Извлекает все дочерние элементы указанного родительского идентификатора, соответствующие имени и типу символа.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Извлекает указанный тип символа, который содержит или ближайший к указанному адресу.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Извлекает указанный тип символа, который содержит или ближайший к определенному относительному виртуальному адресу (RVA).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Извлекает указанный тип символа, который содержит или ближайший к конкретному виртуальному адресу (ва).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Извлекает символ, который содержит указанный токен метаданных.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Проверяет, эквивалентны ли два символа.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Извлекает символ по его уникальному идентификатору.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Извлекает указанный тип символа, который содержит, или ближайший к, заданный относительный виртуальный адрес и смещение.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Извлекает указанный тип символа, который содержит или ближайший к указанному виртуальному адресу и смещению.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Извлекает исходный файл по компилируемого объекта и имени.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Извлекает исходный файл по идентификатору исходного файла.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Получает номера строк в указанном компилируемого объекта и идентификаторе исходного файла.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Получает строки в указанном компилируемого объекта, содержащем указанный адрес.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Получает строки в указанном компилируемого объекта, которые содержат заданный относительный виртуальный адрес.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Находит сведения о номере строки для строк, содержащихся в указанном диапазоне адресов.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Получает строки в указанном компилируемого объекта по исходному файлу и номеру строки.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Извлекает источник, помещенный в хранилище символов поставщиками атрибутов или другими компонентами процесса компиляции.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Извлекает перечислимую последовательность потоков данных отладки.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Извлекает перечисление, позволяющее клиенту выполнять итерацию всех встроенных кадров по заданному адресу.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Извлекает перечисление, позволяющее клиенту выполнять итерацию всех встроенных кадров на указанном относительном виртуальном адресе (RVA).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Извлекает перечисление, позволяющее клиенту выполнять итерацию всех встроенных кадров на указанном виртуальном адресе (ва).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех функций, встроенных, прямо или косвенно, по указанному родительскому символу.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех функций, которые прямо или косвенно связаны с указанным родительским символом и содержатся в указанном диапазоне адресов.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех функций, которые прямо или косвенно связаны с указанным родительским символом и содержатся в указанном относительном виртуальном адресе (RVA).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех функций, которые прямо или косвенно связаны с указанным родительским символом и содержатся в указанном виртуальном адресе (ва).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех функций, встроенных, прямо или косвенно, в указанном исходном файле и номере строки.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех встроенных функций, соответствующих заданному имени.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Возвращает перечисление символов для переменной, которой соответствует указанное значение тега в родительской функции-заглушке ускорителя.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|При наличии соответствующего значения тега этот метод возвращает перечисление символов, содержащихся в указанной родительской функции-заглушке ускорителя, по указанному относительному виртуальному адресу.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Возвращает перечисление символов для встроенных кадров, соответствующих указанному имени встроенной функции.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Возвращает перечисление символов для встраиваемых кадров, соответствующих указанному исходному расположению.|  
  
## <a name="remarks"></a>Remarks  
 Важно вызвать метод [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) после создания `IDiaSession` объекта, и значение, передаваемое `put_loadAddress` методу, должно быть ненулевым — для доступа к любому свойству СИМВОЛА виртуального адреса (ва). Адрес загрузки поступает из любой программы, загруженной в отлаживаемый исполняемый файл. Например, можно вызвать функцию Win32 `GetModuleInformation` , чтобы получить адрес загрузки для исполняемого файла, учитывая обработчик для исполняемого файла.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить `IDiaSession` интерфейс в рамках общей инициализации пакета SDK Dia.  
  
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
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Средств](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Программы](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [идиадатасаурце](../../debugger/debug-interface-access/idiadatasource.md)   
 [Идиадатасаурце:: Опенсессион](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol:: Финдчилдрен](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
