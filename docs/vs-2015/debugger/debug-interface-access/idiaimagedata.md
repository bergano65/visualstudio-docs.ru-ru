---
title: Идиаимажедата | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData interface
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54d09a037fff08b1c34f9a0b5e1fbf018cd10bc3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161401"
---
# <a name="idiaimagedata"></a>IDiaImageData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Предоставляет подробные сведения о базовом расположении и смещениях памяти для модуля или изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaImageData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaImageData` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Извлекает расположение в виртуальной памяти модуля относительно приложения.|  
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Извлекает расположение в виртуальной памяти образа.|  
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Извлекает место в памяти, на котором должно быть основано изображение.|  
  
## <a name="remarks"></a>Remarks  
 Некоторые отладочные потоки (XDATA, PDATA) содержат копии данных, которые также хранятся в образе. Эти объекты потоковых данных можно запрашивать для `IDiaImageData` интерфейса. Дополнительные сведения см. в подразделе "Примечания для вызывающих объектов" этого раздела.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получите этот интерфейс, вызвав метод `QueryInterface` для объекта [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) . Обратите внимание, что не все потоки отладки поддерживают `IDiaImageData` интерфейс. Например, в настоящее время интерфейс поддерживает только потоки XDATA и PDATA `IDiaImageData` .  
  
## <a name="example"></a>Пример  
 В этом примере выполняется поиск всех потоков отладки для любого потока, поддерживающего `IDiaImageData` интерфейс. Если такой поток найден, отображаются некоторые сведения об этом потоке.  
  
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
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
