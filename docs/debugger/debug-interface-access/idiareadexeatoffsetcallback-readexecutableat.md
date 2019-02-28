---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f199db93fa2ea0b3ee2633f9af8a02fff5a4fdf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695821"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Считывает указанное число байтов, начиная с заданного смещения из исполняемого файла.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Параметры
 fileOffset

[in] Смещение в исполняемом файле, должно начаться чтение.

 cbData

[in] Число байтов для чтения.

 pcbData

[out] Возвращает число считанных байтов.

 data[]

[in, out] Массив, который заполняется байтов, считанных из файла.

## <a name="remarks"></a>Примечания
 Этот метод вызывается для загрузки данных в байтах из исполняемого файла с помощью смещения абсолютный код поддержки доступа к интерфейсу отладки. Этот метод вызывается на [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.

## <a name="see-also"></a>См. также раздел
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)