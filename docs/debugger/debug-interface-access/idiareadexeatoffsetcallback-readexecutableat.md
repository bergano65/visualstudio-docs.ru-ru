---
title: 'Идиареадексеатоффсеткаллбакк:: Реадексекутаблеат | Документация Майкрософт'
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
ms.openlocfilehash: d913a229dafb64570728434576716ba396648af3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742831"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Считывает указанное число байтов, начиная с указанного смещения, из исполняемого файла.

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
 филеоффсет

окне Смещение в исполняемом файле, с которого начинается чтение.

 cbData

окне Число байтов для чтения.

 пкбдата

заполняет Возвращает число считанных байтов.

 data[]

[вход, выход] Массив, который заполняется байтами, считанными из файла.

## <a name="remarks"></a>Заметки
 Этот метод вызывается кодом поддержки DIA для загрузки байтов данных из исполняемого файла с использованием абсолютного смещения. Этот метод вызывается для поддержки метода [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>См. также
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)