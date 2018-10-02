---
title: IDiaEnumFrameData | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData interface
ms.assetid: 2ca7fd5a-b2fa-4b3a-9492-0263eafc435b
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a492f11b699aa544e865941e4af389f02e9d3bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573097"
---
# <a name="idiaenumframedata"></a>IDiaEnumFrameData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaEnumFrameData](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumframedata).  
  
Перечисляет различные элементы данных кадров, содержащихся в источнике данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaEnumFrameData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaEnumFrameData`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaEnumFrameData::get__NewEnum](../../debugger/debug-interface-access/idiaenumframedata-get-newenum.md)|Извлекает `IEnumVARIANT Interface` версии этот перечислитель.|  
|[IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)|Возвращает число элементов данных кадра.|  
|[IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)|Извлекает элемент кадра данных с помощью индекса.|  
|[IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)|Извлекает указанное число кадров данных элементов в последовательности перечисления.|  
|[IDiaEnumFrameData::Skip](../../debugger/debug-interface-access/idiaenumframedata-skip.md)|Пропускает указанное число кадров данных элементов в последовательности перечисления.|  
|[IDiaEnumFrameData::Reset](../../debugger/debug-interface-access/idiaenumframedata-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[IDiaEnumFrameData::Clone](../../debugger/debug-interface-access/idiaenumframedata-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[IDiaEnumFrameData::frameByRVA](../../debugger/debug-interface-access/idiaenumframedata-framebyrva.md)|Возвращает кадр, относительный виртуальный адрес (RVA).|  
|[IDiaEnumFrameData::frameByVA](../../debugger/debug-interface-access/idiaenumframedata-framebyva.md)|Возвращает кадр, виртуальный адрес (VA).|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Получить этот интерфейс из [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) метод. Дополнительные сведения см.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить ( `GetEnumFrameData` функции) и использовать ( `ShowFrameData` функции) `IDiaEnumFrameData` интерфейс. См. в разделе [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) интерфейс пример `PrintFrameData` функции.  
  
```cpp#  
  
      IDiaEnumFrameData* GetEnumFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pUnknown    = NULL;  
    REFIID             iid         = __uuidof(IDiaEnumFrameData);  
    IDiaEnumTables*    pEnumTables = NULL;  
    IDiaTable*         pTable      = NULL;  
    ULONG              celt        = 0;  
  
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
  
void ShowFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pEnumFrameData = GetEnumFrameData(pSession);;  
  
    if (pEnumFrameData != NULL)  
    {  
        IDiaFrameData* pFrameData;  
        ULONG celt = 0;  
  
        while(pEnumFrameData->Next(1, &pFrameData, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintFrameData(pFrameData);  
            pFrameData->Release();  
        }  
        pEnumFrameData->Release();   
    }  
}  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** Dia2.h  
  
 **Библиотека:** diaguids.lib  
  
 **Библиотека DLL:** msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



