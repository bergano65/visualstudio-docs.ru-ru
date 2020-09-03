---
title: Идиадатасаурце | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a02eb9048c0e9338e6300fc63666af4db535b3ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198593"
---
# <a name="idiadatasource"></a>IDiaDataSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Инициирует доступ к источнику отладочных символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaDataSource` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Возвращает имя файла для последней ошибки загрузки.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Открывает и готовит файл базы данных программы (PDB) в качестве источника данных отладки.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Открывает и проверяет, совпадает ли файл базы данных программы (PDB) с предоставленными сведениями о сигнатуре. подготавливает pdb-файл в качестве источника данных отладки.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Открывает и готовит данные отладки, связанные с файлом EXE/. dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Подготавливает данные отладки, хранящиеся в файле базы данных программы (. pdb), к которому осуществляется доступ через поток данных в памяти.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Открывает сеанс для запроса символов.|  
  
## <a name="remarks"></a>Remarks  
 Вызов одного из методов Load `IDiaDataSource` интерфейса открывает источник символов. Успешный вызов метода [идиадатасаурце:: опенсессион](../../debugger/debug-interface-access/idiadatasource-opensession.md) возвращает интерфейс [IDiaSession](../../debugger/debug-interface-access/idiasession.md) , который поддерживает запросы к источнику данных. Если метод Load возвращает ошибку, связанную с файлом, то возвращаемое значение метода [идиадатасаурце:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) содержит имя файла, связанного с ошибкой.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс получается путем вызова `CoCreateInstance` функции с идентификатором класса `CLSID_DiaSource` и идентификатором интерфейса `IID_IDiaDataSource` . В примере показано, как получен этот интерфейс.  
  
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
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
