---
title: IDiaDataSource::loadDataForExe | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f95e8a9321ff7ae518e72496289f8ad0c7b4682
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609648"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Открывает и подготавливает данные отладки, связанный с файлом.exe/.dll.

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

## <a name="see-also"></a>См. также раздел
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
