---
title: IDiaDataSource::loadDataFromIStream | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb9b218935085b04ae1a9931733aeca34766aa5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833690"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Подготавливает отладочные данные, хранящиеся в PDB-файл программы, через поток данных в памяти.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>Параметры
 pIStream

[in] <xref:IStream> Объект, представляющий поток данных для использования.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.

|Значение|Описание|
|-----------|-----------------|
|E_PDB_FORMAT|Предпринята попытка получить доступ к файлу с устаревший формат.|
|E_INVALIDARG|Недопустимый параметр.|
|E_UNEXPECTED|Источник данных уже подготовлен.|

## <a name="remarks"></a>Примечания
 Этот метод позволяет данные отладки для исполняемого файла может быть получена из памяти посредством <xref:IStream> объекта.

 Чтобы загрузить PDB-файл без проверки, используйте [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) метод.

 Чтобы проверить PDB-файла с определенным критериям, используйте [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) метод.

 Чтобы получить доступ к процесс загрузки данных (через механизм обратного вызова), используйте [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.

## <a name="see-also"></a>См. также
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)