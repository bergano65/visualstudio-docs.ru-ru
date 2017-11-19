---
title: "IDiaEnumSectionContribs | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSectionContribs interface
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38c73680435816d044c363f55193fba64b33ee44
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsectioncontribs"></a>IDiaEnumSectionContribs
Перечисляет различные раздел материалов, содержащиеся в источнике данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaEnumSectionContribs : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaEnumSectionContribs`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaEnumSectionContribs::get__NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|Извлекает [интерфейса IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) версии этот перечислитель.|  
|[IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)|Возвращает число вклады раздела.|  
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|Извлекает вклады раздел с помощью индекса.|  
|[IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)|Извлекает указанное число вклады раздела в последовательности перечисления.|  
|[IDiaEnumSectionContribs::Skip](../../debugger/debug-interface-access/idiaenumsectioncontribs-skip.md)|Пропускает указанное число вклады раздела в последовательности перечисления.|  
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="note-for-callers"></a>Примечание для клиентов  
 Получить этот интерфейс из [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) метод. Дополнительные сведения см.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить ( `GetEnumSectionContribs` функции) и использовать ( `ShowSectionContribs` функция) `IDiaEnumSectionContribs` интерфейс. Более полный пример использования вклады раздел, в разделе [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) интерфейса.  
  
```C++  
  
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
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)