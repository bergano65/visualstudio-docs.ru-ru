---
title: "IDiaEnumDebugStreams | Microsoft Docs"
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
  - "IDiaEnumDebugStreams - интерфейс"
ms.assetid: 611caf4f-7a5f-4aa4-b909-52feeb3cc752
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumDebugStreams
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Перечисляет различные потоки отладки, содержащихся в источнике данных.  
  
## Синтаксис  
  
```  
IDiaEnumDebugStreams : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaEnumDebugStreams`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaEnumDebugStreams::get\_\_NewEnum](../Topic/IDiaEnumDebugStreams::get__NewEnum.md)|Извлекает `IEnumVARIANT` версия данного перечислителя.|  
|[IDiaEnumDebugStreams::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md)|Извлекает число потоков отладки.|  
|[IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)|Получает поток отладки посредством индекса.|  
|[IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)|Извлекает заданное количество потоков в последовательности перечисления отладки.|  
|[IDiaEnumDebugStreams::Skip](../../debugger/debug-interface-access/idiaenumdebugstreams-skip.md)|Пропустить указанное количество потоков в последовательности перечисления отладки.|  
|[IDiaEnumDebugStreams::Reset](../../debugger/debug-interface-access/idiaenumdebugstreams-reset.md)|Сбросить последовательность перечисления в начало.|  
|[IDiaEnumDebugStreams::Clone](../../debugger/debug-interface-access/idiaenumdebugstreams-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
  
## Заметки  
 Содержимое отладки потоки реализация\-зависимая ячейку и форматов данных недокументированный.  
  
## Замечания для вызывающих объектов  
 Вызовите [IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md) метод получения  `IDiaEnumDebugStreams` объект.  
  
## Пример  
 В этом примере показано, как получить доступ к потоки данных, доступные из этого интерфейса.  См. [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) интерфейс для реализации   `PrintStreamData` функция.  
  
```cpp#  
void DumpAllDebugStreams( IDiaSession* pSession)  
{  
    IDiaEnumDebugStreams* pEnumStreams;  
  
    wprintf(L"\n\n*** DEBUG STREAMS\n\n");  
    // Retrieve an enumerated sequence of debug data streams  
    if(pSession->getEnumDebugStreams(&pEnumStreams) == S_OK)  
    {  
        IDiaEnumDebugStreamData* pStream;  
        ULONG celt = 0;  
  
        for(; pEnumStreams->Next(1, &pStream, &celt) == S_OK; pStream = NULL)  
        {  
            PrintStreamData(pStream);  
            pStream->Release();  
        }  
        pEnumStreams->Release();  
    }  
    else  
    {  
      wprintf(L"Failed to get any debug streams!\n");  
    }  
    wprintf(L"\n");  
}  
```  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)