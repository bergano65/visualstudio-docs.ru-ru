---
title: "IDiaImageData | Microsoft Docs"
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
  - "IDiaImageData - интерфейс"
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaImageData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Предоставляет подробные сведения о базовых смещений расположения и памяти модуля или образа.  
  
## Синтаксис  
  
```  
IDiaImageData : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaImageData`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaImageData::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Извлекает расположение в виртуальной памяти модуля по отношению к приложению.|  
|[IDiaImageData::get\_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Извлекает расположение в виртуальной памяти образа.|  
|[IDiaImageData::get\_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Извлекает область памяти, где образ должен быть основан.|  
  
## Заметки  
 Некоторые потоки отладки \(XDATA \- PDATA\) содержат копии данных, хранящихся в режиме.  Эти объекты данных потока можно запросить `IDiaImageData` интерфейс.  См. "примечания для вызывающих объектов" этого раздела.  
  
## Замечания для вызывающих объектов  
 Для получения этого интерфейса нужно вызвать метод `QueryInterface` на  [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) объект.  Обратите внимание, что не все потоки поддерживают отладки `IDiaImageData` интерфейс.  Например, в настоящее время потоки поддерживают только XDATA и PDATA `IDiaImageData` интерфейс.  
  
## Пример  
 Этот пример находит все потоки отладки для любого потока, поддерживающий `IDiaImageData` интерфейс.  Если такой поток найден, то некоторые сведения об этом потоке.  
  
```cpp#  
void ShowImageData(IDiaSession *pSession)  
{  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumDebugStreams> pStreamsList;  
        HRESULT hr;  
  
        hr = pSession->getEnumDebugStreams(&pStreamsList);  
        if (SUCCEEDED(hr))  
        {  
            LONG numStreams = 0;  
            hr = pStreamsList->get_Count(&numStreams);  
            if (SUCCEEDED(hr))  
            {  
                ULONG fetched = 0;  
                for (LONG i = 0; i < numStreams; i++)  
                {  
                    CComPtr<IDiaEnumDebugStreamData> pStream;  
                    hr = pStreamsList->Next(1,&pStream,&fetched);  
                    if (fetched == 1)  
                    {  
                        CComPtr<IDiaImageData> pImageData;  
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),  
                                                     (void **)&pImageData);  
                        if (SUCCEEDED(hr))  
                        {  
                            CComBSTR name;  
                            hr = pStream->get_name(&name);  
                            if (SUCCEEDED(hr))  
                            {  
                                wprintf(L"Stream %s:\n",(BSTR)name);  
                            }  
                            else  
                            {  
                                wprintf(L"Failed to get name of stream\n");  
                            }  
  
                            ULONGLONG imageBase = 0;  
                            if (pImageData->get_imageBase(&imageBase) == S_OK)  
                            {  
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);  
                            }  
  
                            DWORD relVA = 0;  
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)  
                            {  
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);  
                            }  
  
                            ULONGLONG va = 0;  
                            if (pImageData->get_virtualAddress(&va) == S_OK)  
                            {  
                                wprintf(L"  virtual address = 0x%0I64x\n", va);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)