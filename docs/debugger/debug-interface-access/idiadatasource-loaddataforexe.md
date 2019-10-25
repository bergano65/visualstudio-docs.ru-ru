---
title: 'Идиадатасаурце:: Лоаддатафорексе | Документация Майкрософт'
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
ms.openlocfilehash: 7a86abb00ebc090c37f03a5533376ae0b9c3e8ae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744959"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Открывает и готовит данные отладки, связанные с файлом EXE/. dll.

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

окне Путь к exe-или DLL-файлу.

searchPath

окне Альтернативный путь для поиска данных отладки.

пкаллбакк

окне Интерфейс `IUnknown` для объекта, поддерживающего интерфейс обратного вызова отладки, например [идиалоадкаллбакк](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [Идиареадексеатоффсеткаллбакк](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)и/или интерфейс [идиареадексеатрвакаллбакк](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. В следующей таблице показаны некоторые возможные коды ошибок для этого метода.

|значения|Описание|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Не удалось открыть файл, или файл имеет недопустимый формат.|
|E_PDB_FORMAT|Попытка доступа к файлу с устаревшим форматом.|
|E_PDB_INVALID_SIG|Сигнатура не совпадает.|
|E_PDB_INVALID_AGE|Возраст не соответствует.|
|E_INVALIDARG|Недопустимый параметр.|
|E_UNEXPECTED|Источник данных уже подготовлен.|

## <a name="remarks"></a>Заметки
В заголовке Debug файла exe/. DLL называется связанное расположение данных отладки.

Этот метод считывает заголовок Debug, а затем ищет и готовит данные отладки. Ход выполнения поиска может при необходимости передаваться и контролироваться с помощью обратных вызовов. Например, [идиалоадкаллбакк:: нотифидебугдир](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) вызывается, когда метод `IDiaDataSource::loadDataForExe` находит и обрабатывает каталог отладки.

Интерфейсы [идиареадексеатоффсеткаллбакк](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) и [идиареадексеатрвакаллбакк](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) позволяют клиентскому приложению предоставлять альтернативные методы для чтения данных из исполняемого файла, если доступ к файлу напрямую через стандартный файловый ввод-вывод.

Чтобы загрузить PDB-файл без проверки, используйте метод [идиадатасаурце:: лоаддатафромпдб](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

Чтобы проверить PDB-файл на соответствие конкретным критериям, используйте метод [идиадатасаурце:: лоадандвалидатедатафромпдб](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Чтобы загрузить PDB-файл непосредственно из памяти, используйте метод [идиадатасаурце:: лоаддатафромистреам](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

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
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
