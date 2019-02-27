---
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf423ddc91926fb04adac849783b7c26b4c4f720
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708112"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Считывает указанное число байтов, начиная с указанного относительного виртуального адреса (RVA) из исполняемого файла.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT ReadExecutableAtRVA ( 
   DWORD  relativeVirtualAddress,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Параметры
 `relativeVirtualAddress`

[in] RVA в исполняемом файле должно начаться чтение.

 `cbData`

[in] Число байтов для чтения.

 `pcbData`

[out] Возвращает число считанных байтов.

 `data[]`

[in, out] Массив, который заполняется байтов, считанных из файла.

## <a name="remarks"></a>Примечания
 Этот метод вызывается в коде поддержки доступа к интерфейсу отладки для загрузки данных в байтах из исполняемого файла с помощью относительного виртуального адреса. Этот метод вызывается на [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.

## <a name="see-also"></a>См. также раздел
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)