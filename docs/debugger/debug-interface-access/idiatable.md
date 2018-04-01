---
title: IDiaTable | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8f596d2c51c5d5e543ed67212662c5096ea2e4eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiatable"></a>IDiaTable
Перечисляет таблицы источника данных доступа к интерфейсу отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaTable`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Извлекает [интерфейса IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) версии этот перечислитель.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Возвращает имя таблицы.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Возвращает число элементов в таблице.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Извлекает ссылку на определенную запись индекс.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс реализует `IEnumUnknown` методов перечисления в пространстве имен Microsoft.VisualStudio.OLE.Interop. `IEnumUnknown` Интерфейс перечисления является более эффективным для прохода по содержимое таблицы, чем [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) и [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md) методы.  
  
 Интерпретация `IUnknown` интерфейс возвращаемый либо `IDiaTable::Item` метода или `Next` метода (в пространстве имен Microsoft.VisualStudio.OLE.Interop) зависит от типа таблицы. Например если `IDiaTable` интерфейс представляет список подставляемого источников `IUnknown` интерфейса должны запрашиваться для [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получить этот интерфейс, вызвав [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) или [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md) методы.  
  
 Следующие интерфейсы реализуются с помощью `IDiaTable` интерфейса (то есть, вы можете запросить `IDiaTable` интерфейс для одного из следующих интерфейсов):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Пример  
 Первая функция `ShowTableNames`, отображаются имена всех таблиц в сеансе. Вторая функция `GetTable`, выполняет все таблицы для таблицы, который реализует указанный интерфейс. Третья функция `UseTable`, показано, как использовать `GetTable` функции.  
  
> [!NOTE]
>  `CDiaBSTR`Представляет класс-оболочку `BSTR` и автоматически обрабатывает освобождая строку, когда экземпляр выходит за пределы области.  
  
```C++  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)