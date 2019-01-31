---
title: IDiaSession::getEnumTables | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 748da3122a6ac15e8b6bd6101a6a97f504d35fc6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070998"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Возвращает перечислитель для всех таблиц, содержащихся в хранилище символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT getEnumTables (   
   IDiaEnumTables** ppEnumTables  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnumTables`  
 [out] Возвращает [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) объекта. Этот интерфейс можно используйте для перечисления таблиц в хранилище символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
 В этом примере представлены общие функции, которая использует `getEnumTables` метод для получения объекта определенного перечислителя. При обнаружении перечислитель, функция возвращает указатель, который может быть приведен к требуемого интерфейса; в противном случае функция возвращает `NULL`.  
  
```C++  
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)  
{  
    IUnknown *pUnknown = NULL;  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumTables> pEnumTables;  
        if (pSession->getEnumTables(&pEnumTables) == S_OK)  
        {  
             CComPtr<IDiaTable> pTable;  
             DWORD celt = 0;  
             while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&  
                   celt == 1)  
             {  
                  if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)  
                  {  
                       break;  
                  }  
                  pTable = NULL;  
             }  
        }  
    }  
    return(pUnknown);  
}  
```  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)