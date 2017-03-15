---
title: "IDiaDataSource::loadDataForExe | Microsoft Docs"
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
  - "IDiaDataSource::loadDataForExe - метод"
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Открытые и откладывается данных отладки, связанные с файлом .exe\/.dll.  
  
## Синтаксис  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### Параметры  
 executable  
 \[in\] путь к exe\- или dll\-файла.  
  
 searchPath  
 \[in\] альтернативный путь для поиска отладочные данные.  
  
 pCallback  
 \[in\] `IUnknown` интерфейс для объекта, который поддерживает интерфейс обратного вызова, как отлаживать  [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)"  [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)"  [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)или  [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) интерфейсы.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  В следующей таблице показаны некоторые из возможных кодов ошибок для данного метода.  
  
|Значение|Описание|  
|--------------|--------------|  
|E\_PDB\_NOT\_FOUND|Не удалось открыть файл или же файл имеет недопустимый формат.|  
|E\_PDB\_FORMAT|Предпринята попытка получить доступ к файлу с устаревшими форматом.|  
|E\_PDB\_INVALID\_SIG|Сигнатура не совпадает.|  
|E\_PDB\_INVALID\_AGE|Age.|  
|E\_INVALIDARG|Недопустимый параметр.|  
|E\_UNEXPECTED|Источник данных уже был подготовлен.|  
  
## Заметки  
 Заголовок отладки, связанное имен файлов .exe\/.dll место отладки данных.  
  
 Этот метод считывает заголовок отладки, а затем ищет и подготавливает данные отладки.  Ход выполнения поиска может также быть сообщается и управляется через обратные вызовы.  Например, [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) вызывается, когда  `IDiaDataSource::loadDataForExe` метод находит и обрабатывает каталог отладки.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) и  [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) интерфейсы позволяют клиентскому приложению предоставить альтернативные методы для чтения данных из исполняемого файла, если файл нельзя получить доступ непосредственно через ввода\-вывода. стандартного файла.  
  
 Чтобы загрузить файл pdb без проверки, используйте [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) метод.  
  
 Чтобы проверить файл pdb для определенных критериев, используйте [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) метод.  
  
 Чтобы загрузить файл pdb непосредственно из памяти, используйте [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) метод.  
  
## Пример  
  
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
  
## См. также  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)