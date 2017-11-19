---
title: "IDiaEnumSourceFiles | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSourceFiles interface
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd3e50e1b53a56342b5ab344ec54180001fa80
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsourcefiles"></a>IDiaEnumSourceFiles
Перечисляет различные исходные файлы, содержащиеся в источнике данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaEnumSourceFiles : IUknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaEnumSourceFiles`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaEnumSourceFiles::get__NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|Извлекает `IEnumVARIANT Interface` версии этот перечислитель.|  
|[IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|Возвращает число исходных файлов.|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|Получает исходный файл с помощью индекса.|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Извлекает указанное число исходных файлов в последовательности перечисления.|  
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|Пропускает указанное число исходных файлов в последовательности перечисления.|  
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получить этот интерфейс, вызвав `QueryInterface` метод [IDiaTable](../../debugger/debug-interface-access/idiatable.md) объекта. Дополнительные сведения см.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить `IDiaEnumSourceFiles` интерфейс из списка таблиц в объекте сеанса доступа к интерфейсу отладки. Пример доступа к информация об исходном файле, в разделе [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) интерфейса.  
  
```C++  
  
IDiaEnumSourceFiles* GetEnumSourceFiless(IDiaSession *pSession)  
{  
    IDiaEnumSourceFiles * pUnknown    = NULL;  
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);  
    IDiaEnumTables*       pEnumTables = NULL;  
    IDiaTable*            pTable      = NULL;  
    ULONG                 celt        = 0;  
  
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
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)