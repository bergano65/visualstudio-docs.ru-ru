---
title: IDiaDataSource::loadDataForExe | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e9e68acd3b8c87bb3fa7a609380a2afe8bb9bee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Открывает и подготовить данные отладки, связанный с файлом.exe/.dll.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 исполняемый файл  
 [in] Путь к файлу .exe или .dll.  
  
 searchPath  
 [in] Альтернативный путь для поиска данных отладки.  
  
 pCallback  
 [in] `IUnknown` Интерфейс для объекта, который поддерживает интерфейс обратного вызова отладки, такие как [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), и/или [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) интерфейсов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. В следующей таблице показаны некоторые кодов ошибок для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Не удалось открыть файл или файл имеет недопустимый формат.|  
|E_PDB_FORMAT|Предпринята попытка доступа к файлу с устаревший формат.|  
|E_PDB_INVALID_SIG|Подпись не соответствует.|  
|E_PDB_INVALID_AGE|Срок действия не соответствует.|  
|E_INVALIDARG|Недопустимый параметр.|  
|E_UNEXPECTED|Источник данных уже был подготовлен.|  
  
## <a name="remarks"></a>Примечания  
 Заголовок отладки файла.exe/.dll имен расположение данных связанного отладки.  
  
 Этот метод считывает заголовок отладки и затем ищет и подготавливает данные отладки. Ход выполнения поиска при необходимости сообщил и управляется с помощью обратных вызовов. Например [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) при вызове `IDiaDataSource::loadDataForExe` метод находит и обрабатывает каталог отладки.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) и [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) интерфейсы позволяют клиентскому приложению, предоставляют альтернативные методы для чтения данных из исполняемого объекта файл появляется, когда файл не может осуществляться непосредственно с помощью стандартных файлового ввода-вывода.  
  
 Чтобы загрузить PDB-файла без проверки, используйте [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) метод.  
  
 Чтобы проверить файл PDB-файл на соответствие определенным критериям, используйте [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) метод.  
  
 Чтобы загрузить PDB-файл непосредственно из памяти, используйте [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) метод.  
  
## <a name="example"></a>Пример  
  
```C++  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)