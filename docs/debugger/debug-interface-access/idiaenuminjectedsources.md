---
title: "IDiaEnumInjectedSources | Microsoft Docs"
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
  - "IDiaEnumInjectedSources - интерфейс"
ms.assetid: f97e2392-22e1-48da-b7ce-ad94c8b684b0
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaEnumInjectedSources
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Перечисляет различные источники впрыснутые, содержащихся в источнике данных.  
  
## Синтаксис  
  
```  
IDiaEnumInjectedSources : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaEnumInjectedSources`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaEnumInjectedSources::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenuminjectedsources-get-newenum.md)|Извлекает [интерфейс IEnumVARIANT](http://msdn.microsoft.com/ru-ru/139e3c93-faef-4003-9079-e0e94494db3e) версия данного перечислителя.|  
|[IDiaEnumInjectedSources::get\_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)|Извлекает число впрыснутых источников.|  
|[IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)|Получает введенный источник посредством индекса.|  
|[IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)|Извлекает заданное количество впрыснутых источников в последовательности перечисления.|  
|[IDiaEnumInjectedSources::Skip](../Topic/IDiaEnumInjectedSources::Skip.md)|Пропустить указанное количество впрыснутых источников в последовательности перечисления.|  
|[IDiaEnumInjectedSources::Reset](../../debugger/debug-interface-access/idiaenuminjectedsources-reset.md)|Сбросить последовательность перечисления в начало.|  
|[IDiaEnumInjectedSources::Clone](../../debugger/debug-interface-access/idiaenuminjectedsources-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
  
## Заметки  
  
## Замечания для вызывающих объектов  
 Этот интерфейс полученного вызовом метода [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md) метод с именем конкретного файла источника или путем вызова  [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) метод с идентификатором GUID  `IDiaEnumInjectedSources` интерфейс.  
  
## Пример  
 В этом примере показано, как получить \( `GetEnumInjectedSources` \(функция\) и использует  `DumpAllInjectedSources` функция\)  `IDiaEnumInjectedSources` интерфейс.  См. [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) интерфейс для реализации   `PrintPropertyStorage` функция.  Для альтернативного вывода см. в разделе [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) интерфейс.  
  
```cpp#  
  
IDiaEnumInjectedSources* GetEnumInjectedSources(IDiaSession *pSession)  
{  
    IDiaEnumInjectedSources* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumInjectedSources);  
    IDiaEnumTables*          pEnumTables = NULL;  
    IDiaTable*               pTable      = NULL;  
    ULONG                    celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
  
void DumpAllInjectedSources( IDiaSession* pSession)  
{  
    IDiaEnumInjectedSources* pEnumInjSources;  
  
    pEnumInjSources = GetEnumInjectedSources(pSession);  
    if (pEnumInjSources != NULL)  
    {  
        IDiaInjectedSource* pInjSource;  
        ULONG celt = 0;  
  
        while(pEnumInjSources->Next(1, &pInjSource, &celt) == S_OK &&  
              celt == 1)  
        {  
            IDiaPropertyStorage *pPropertyStorage;  
            if (pInjSource->QueryInterface(__uuidof(IDiaPropertyStorage),  
                                           (void **)&pPropertyStorage) == S_OK)  
            {  
                PrintPropertyStorage(pPropertyStorage);  
                pPropertyStorage->Release();  
            }  
            pInjSource->Release();  
        }  
        pEnumInjSources->Release();  
    }  
}  
```  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)