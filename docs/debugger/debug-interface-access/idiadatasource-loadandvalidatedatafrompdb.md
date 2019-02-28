---
title: IDiaDataSource::loadAndValidateDataFromPdb | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5426e27d7b100c42cd571935b1634d6dbd6e990f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626145"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Открывает и проверяет соответствие подписи сведений, предоставленных в PDB-файл программы и подготавливает PDB-файл в качестве источника данных отладки.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT loadAndValidateDataFromPdb ( 
   LPCOLESTR pdbPath,
   GUID*     pcsig70,
   DWORD     sig,
   DWORD     age
);
```

#### <a name="parameters"></a>Параметры
`pdbPath`

[in] Путь к PDB-файл.

`pcsig70`

[in] Подпись GUID для проверки подписи файла PDB-файл. Файлы только PDB-файл в [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] и более поздней версии имеют подписи GUID.

`sig`

[in] 32-разрядных подпись для проверки подписи файла PDB-файл.

`age`

[in] Значение возраста, чтобы проверить. Возраст необязательно соответствует любому значению известных времени, он используется для определения того, если PDB-файл не синхронизирован с соответствующим файлом .exe.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.

|Значение|Описание|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Не удалось открыть файл или файл имеет недопустимый формат.|
|E_PDB_FORMAT|Предпринята попытка получить доступ к файлу с устаревший формат.|
|E_PDB_INVALID_SIG|Подпись не совпадает.|
|E_PDB_INVALID_AGE|Возраст не совпадает.|
|E_INVALIDARG|Недопустимый параметр.|
|E_UNEXPECTED|Источник данных уже подготовлен.|

## <a name="remarks"></a>Примечания
PDB-файл содержит значения, подпись и возраст. Эти значения, реплицируются в файле .exe или .dll, который соответствует PDB-файл. Перед подготовкой источника данных, этот метод проверяет соответствие значений, указанных сигнатура и возраст именованный PDB-файл.

Чтобы загрузить PDB-файл без проверки, используйте [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) метод.

Чтобы получить доступ к процесс загрузки данных (через механизм обратного вызова), используйте [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.

Чтобы загрузить PDB-файл непосредственно из памяти, используйте [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) метод.

## <a name="example"></a>Пример

```C++
IDiaDataSource* pSource;  // Previously created data source.
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);
DWORD expectedFileSignature = 0x12345678;
DWORD expectedAge           = 128;

HRESULT hr;
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",
                                          &expectedGUIDSignature,
                                          expectedFileSignature,
                                          expectedAge);
if (FAILED(hr))
{
    // Report an error
}

```

## <a name="see-also"></a>См. также раздел
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
