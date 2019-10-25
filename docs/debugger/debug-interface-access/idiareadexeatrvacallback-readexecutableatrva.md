---
title: 'Идиареадексеатрвакаллбакк:: Реадексекутаблеатрва | Документация Майкрософт'
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
ms.openlocfilehash: ca1b1ec2bea56ad167951ad8b60cf849bd22e315
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742787"
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

окне RVA в исполняемом файле, с которого начинается чтение.

 `cbData`

окне Число байтов для чтения.

 `pcbData`

заполняет Возвращает число считанных байтов.

 `data[]`

[вход, выход] Массив, который заполняется байтами, считанными из файла.

## <a name="remarks"></a>Заметки
 Этот метод вызывается кодом поддержки DIA для загрузки байт данных из исполняемого файла с использованием относительного виртуального адреса. Этот метод вызывается для поддержки метода [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>См. также
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)