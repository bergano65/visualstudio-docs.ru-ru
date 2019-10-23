---
title: VSG_DEFAULT_RUN_FILENAME | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 835e2cec19e36418091e094abd2ec76bd6403398
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734832"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Определяет имя файла журнала графики по умолчанию.

## <a name="syntax"></a>Синтаксис

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Параметры
 `filename` Имя файла журнала графики, присваиваемое по умолчанию файлу журнала графики при захвате данных графики программными средствами.

## <a name="value"></a>значения
 Строковый литерал, который представляет имя файла журнала графики. По умолчанию это "default.vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Заметки
 Если определен символ препроцессора `DONT_SAVE_VSGLOG_TO_TEMP`, имя файла является относительным для текущего каталога захватываемого приложения или представляет собой абсолютный путь; в противном случае это имя относительно каталога временных файлов пользователя, которое не может быть абсолютным путем.

 Чтобы изменить имя файла, необходимо переопределить его перед включением `vsgcapture.h` в программу.

## <a name="example"></a>Пример
 В следующем примере показано, как изменить имя файла захвата по умолчанию:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>См. также
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)