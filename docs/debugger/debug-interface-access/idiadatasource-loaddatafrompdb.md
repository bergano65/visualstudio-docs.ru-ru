---
title: 'Идиадатасаурце:: Лоаддатафромпдб | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7526ba6e62c9df22a2338adc80f5d56578502cdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744937"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Открывает и готовит файл базы данных программы (PDB) в качестве источника данных отладки.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Параметры
pdbPath

окне Путь к PDB-файлу.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.

|значения|Описание|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Не удалось открыть файл или определить, что файл имеет недопустимый формат.|
|E_PDB_FORMAT|Попытка доступа к файлу с устаревшим форматом.|
|E_INVALIDARG|Недопустимый параметр.|
|E_UNEXPECTED|Источник данных уже подготовлен.|

## <a name="remarks"></a>Заметки
Этот метод загружает отладочные данные непосредственно из PDB-файла.

Чтобы проверить PDB-файл на соответствие конкретным критериям, используйте метод [идиадатасаурце:: лоадандвалидатедатафромпдб](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Чтобы получить доступ к процессу загрузки данных (посредством механизма обратного вызова), используйте метод [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Чтобы загрузить PDB-файл непосредственно из памяти, используйте метод [идиадатасаурце:: лоаддатафромистреам](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Пример

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>См. также
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
