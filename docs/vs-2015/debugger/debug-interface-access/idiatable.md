---
title: Идиатабле | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b9c9f85ffbf4eed2fdc305a64bd3f32822dacd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682791"
---
# <a name="idiatable"></a>IDiaTable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Перечисляет таблицу источника данных DIA.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaTable` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Извлекает версию [интерфейса IEnumVARIANT](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) этого перечислителя.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Возвращает имя таблицы.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Возвращает количество элементов в таблице.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Извлекает ссылку на определенный индекс записи.|  
  
## <a name="remarks"></a>Remarks  
 Этот интерфейс реализует `IEnumUnknown` методы перечисления в пространстве имен Microsoft. VisualStudio. OLE. Interop. `IEnumUnknown`Интерфейс перечисления гораздо более эффективен для перебора содержимого таблицы по сравнению с методами [идиатабле:: Get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) и [идиатабле:: Item](../../debugger/debug-interface-access/idiatable-item.md) .  
  
 Интерпретация `IUnknown` интерфейса, возвращаемого либо `IDiaTable::Item` методом, либо `Next` методом (в пространстве имен Microsoft. VisualStudio. OLE. Interop) зависит от типа таблицы. Например, если `IDiaTable` интерфейс представляет список внедренных источников, то интерфейс `IUnknown` должен быть запрошен для интерфейса [идиаинжектедсаурце](../../debugger/debug-interface-access/idiainjectedsource.md) .  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получите этот интерфейс, вызвав методы [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) или [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .  
  
 В интерфейсе реализуются следующие интерфейсы `IDiaTable` (то есть можно запросить `IDiaTable` интерфейс для одного из следующих интерфейсов):  
  
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Пример  
 Первая функция, `ShowTableNames` , отображает имена всех таблиц в сеансе. Вторая функция, `GetTable` выполняет поиск по всем таблицам таблицы, реализующей указанный интерфейс. Третья функция, `UseTable` , показывает, как использовать `GetTable` функцию.  
  
> [!NOTE]
> `CDiaBSTR` класс, который заключает в оболочку `BSTR` и автоматически обрабатывает освобождение строки, когда экземпляр выходит из области действия.  
  
```cpp#  
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
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
