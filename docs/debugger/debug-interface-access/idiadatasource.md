---
title: IDiaDataSource | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48e248e537749983293bbeefd60098eabcf70b2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiadatasource"></a>IDiaDataSource
Инициирует доступ к источнику из символов отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaDataSource`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Получает имя файла для последнюю ошибку загрузки.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Открывает и подготавливает PDB-файл программы, как источник данных отладки.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Открывает и проверяет соответствие PDB-файл программы подписи информация; Подготавливает PDB-файл в качестве источника данных отладки.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Открывает и подготовить данные отладки, связанный с файлом.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Подготавливает отладочные данные, хранящиеся в PDB-файл программы, доступных через поток данных в памяти.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Открывается сеанс для выполнения запросов к символы.|  
  
## <a name="remarks"></a>Примечания  
 Вызов одного из методов загрузки `IDiaDataSource` интерфейс Открытие источника символа. Для успешного вызова [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) возвращает [IDiaSession](../../debugger/debug-interface-access/idiasession.md) интерфейс, который поддерживает запросы к источнику данных. Если метод load возвращает ошибки, связанной с файлом то [IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) метод возвращает значение содержит имя файла, с которым связана ошибка.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс можно получить, вызвав `CoCreateInstance` функция с идентификатором класса `CLSID_DiaSource` и идентификатор интерфейса `IID_IDiaDataSource`. В примере показано, как получить этот интерфейс.  
  
## <a name="example"></a>Пример  
  
```C++  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)