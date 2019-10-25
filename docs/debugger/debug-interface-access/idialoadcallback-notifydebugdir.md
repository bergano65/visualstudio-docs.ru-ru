---
title: 'Идиалоадкаллбакк:: Нотифидебугдир | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743089"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Вызывается при обнаружении каталога отладки в exe-файле.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Параметры
 `fExecutable`

[входные файлы] `TRUE`, если каталог отладки считывается из исполняемого файла (а не из файл. dbg).

 `cbData`

окне Число байтов данных в каталоге отладки.

 `data[]`

окне Массив, который заполняется каталогом отладки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. Код возврата обычно игнорируется.

## <a name="remarks"></a>Заметки
 Метод [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) вызывает этот обратный вызов при обнаружении каталога отладки во время обработки исполняемого файла.

 Этот метод устраняет потребность клиента в реконструировании исполняемого файла и/или файл отладки для поддержки отладочной информации, отличной от найденной в PDB-файле. С этими данными клиент может распознать тип доступных отладочных сведений и определить, находится ли он в исполняемом или DBG файле.

 Большинству клиентов этот обратный вызов не нужен, так как метод `IDiaDataSource::loadDataForExe` прозрачно открывает файлы PDB и dbg при необходимости для обслуживания символов.

## <a name="see-also"></a>См. также
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)