---
title: IDiaDataSource | Документация Майкрософт
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
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2abe262ee42d1a22e37e60446f3c44581e40078c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249656"
---
# <a name="idiadatasource"></a>IDiaDataSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Инициирует доступ к источнику отладочные символы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaDataSource`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Получает имя файла для последней ошибки загрузки.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Открывает и подготавливает PDB-файл программы, как источник данных отладки.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Открывает и проверяет, что PDB-файл программы соответствует сигнатуре информация; Подготавливает PDB-файл как источник данных отладки.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Открывает и подготавливает данные отладки, связанный с файлом.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Подготавливает отладочные данные, хранящиеся в PDB-файл программы, через поток данных в памяти.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Открывает сеанс для выполнения запросов к символы.|  
  
## <a name="remarks"></a>Примечания  
 Вызов одного из методов нагрузки `IDiaDataSource` интерфейса открывает источник символов. Успешный вызов [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) возвращает [IDiaSession](../../debugger/debug-interface-access/idiasession.md) интерфейс, который поддерживает запросы к источнику данных. Если метод load возвращает ошибку с файлами то [IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) метод вернуть значение содержит имя файла, с которым связана ошибка.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс получается путем вызова `CoCreateInstance` функции с идентификатором класса `CLSID_DiaSource` и идентификатор интерфейса `IID_IDiaDataSource`. В примере показано, как этот интерфейс получается.  
  
## <a name="example"></a>Пример  
  
```cpp#  
  
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
  
 Библиотеки DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)



