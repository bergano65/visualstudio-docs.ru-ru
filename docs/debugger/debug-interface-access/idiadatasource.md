---
title: IDiaDataSource | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b8618cc3484584430bbe3ae3fde59b6e5d5fc78
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612365"
---
# <a name="idiadatasource"></a>IDiaDataSource
Инициирует доступ к источнику отладочные символы.

## <a name="syntax"></a>Синтаксис

```
IDiaDataSource : IUnknown
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

DLL: msdia80.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
