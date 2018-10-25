---
title: IDiaDataSource::loadDataForExe | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5276c0feefd53eb31e636ed19deadd79bbb3f413
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894421"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Открывает и подготавливает данные отладки, связанный с файлом.exe/.dll.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] Альтернативный путь для поиска данные отладки.  
  
 pCallback  
 [in] `IUnknown` Интерфейс для объекта, который поддерживает интерфейс обратного вызова отладки, такие как [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), и/или [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) интерфейсов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Ниже приведены некоторые из кодов ошибок для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Не удалось открыть файл или файл имеет недопустимый формат.|  
|E_PDB_FORMAT|Предпринята попытка получить доступ к файлу с устаревший формат.|  
|E_PDB_INVALID_SIG|Подпись не совпадает.|  
|E_PDB_INVALID_AGE|Возраст не совпадает.|  
|E_INVALIDARG|Недопустимый параметр.|  
|E_UNEXPECTED|Источник данных уже подготовлен.|  
  
## <a name="remarks"></a>Примечания  
 Заголовок debug файла.exe/.dll имена, расположение данных связанного отладки.  
  
 Этот метод считывает заголовок отладки и затем выполняет поиск и подготавливает данные отладки. При необходимости ход выполнения поиска сообщаемые и управляемые с помощью обратных вызовов. Например [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) при вызове `IDiaDataSource::loadDataForExe` метод находит и обрабатывает каталога отладки.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) и [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) интерфейсы позволяют клиентскому приложению для предоставления альтернативные методы для чтения данных из исполняемого файла, когда файл не удается получить непосредственно с помощью стандартных файлового ввода-вывода.  
  
 Чтобы загрузить PDB-файл без проверки, используйте [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) метод.  
  
 Чтобы проверить PDB-файла с определенным критериям, используйте [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) метод.  
  
 Чтобы загрузить PDB-файл непосредственно из памяти, используйте [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) метод.  
  
## <a name="example"></a>Пример  
  
```cpp#  
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



