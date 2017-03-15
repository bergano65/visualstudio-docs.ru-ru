---
title: "IDiaEnumSectionContribs | Microsoft Docs"
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
  - "IDiaEnumSectionContribs - интерфейс"
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaEnumSectionContribs
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Перечисляет различные вклады раздела, содержащихся в источнике данных.  
  
## Синтаксис  
  
```  
IDiaEnumSectionContribs : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaEnumSectionContribs`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaEnumSectionContribs::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|Извлекает [интерфейс IEnumVARIANT](http://msdn.microsoft.com/ru-ru/139e3c93-faef-4003-9079-e0e94494db3e) версия данного перечислителя.|  
|[IDiaEnumSectionContribs::get\_Count](../Topic/IDiaEnumSectionContribs::get_Count.md)|Извлекает число вкладов раздела.|  
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|Извлекает вклады раздела посредством индекса.|  
|[IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)|Извлекает заданное количество вкладов раздела в последовательности перечисления.|  
|[IDiaEnumSectionContribs::Skip](../Topic/IDiaEnumSectionContribs::Skip.md)|Пропустить указанное количество вкладов раздела в последовательности перечисления.|  
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|Сбросить последовательность перечисления в начало.|  
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
  
## Заметки  
  
## Примечание для вызывающих объектов  
 Для получения этого интерфейса из [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) метод.  См. пример.  
  
## Пример  
 В этом примере показано, как получить \( `GetEnumSectionContribs` \(функция\) и использует  `ShowSectionContribs` функция\)  `IDiaEnumSectionContribs` интерфейс.  Для более полного примера см. в разделе вкладов использования. [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) интерфейс.  
  
```cpp#  
  
      IDiaEnumSectionContribs* GetEnumSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumSectionContribs);  
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
  
void ShowSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pEnumSectionContribs;  
  
    pEnumSectionContribs = GetEnumSectionContribs(pSession);  
    if (pSectionContrib != NULL)  
    {  
        IDiaSectionContrib* pSectionContrib;  
        ULONG celt = 0;  
  
        while(pEnumSectionContribs->Next(1, &pSectionContrib, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintSectionContrib(pSectionContrib, pSession);  
            pSectionContrib->Release();  
        }  
        pSectionContrib->Release();   
    }  
}  
```  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)