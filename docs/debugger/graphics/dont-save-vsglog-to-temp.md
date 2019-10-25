---
title: DONT_SAVE_VSGLOG_TO_TEMP | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40f3c3c22de6b4b0ebdbdf2dfc953f4cb1c9b5e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736081"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Определяет своим наличием, нужно ли сохранять файл журнала графики в каталог временных файлов пользователя.

## <a name="syntax"></a>Синтаксис

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>значения
 Символ препроцессора, который имеет наличие или отсутствие определяет, сохраняется ли файл журнала графики в каталоге временных файлов пользователя. Если этот символ определен, то имя файла, определенное `VSG_DEFAULT_RUN_FILENAME`, задается относительно текущего каталога отслеживаемого приложения или является абсолютным путем. в противном случае имя файла, определенное `VSG_DEFAULT_RUN_FILENAME`, задается относительно каталога временных файлов пользователя и не может быть абсолютным путем.

## <a name="remarks"></a>Заметки
 В зависимости от привилегий пользователя файл журнала графики может быть недоступен для сохранения в произвольном месте. Рекомендуется сохранять журналы графики в каталоге временных файлов пользователя или в другом известном расположении, если вы не знаете, может ли пользователь выбрать нужное расположение.

 Чтобы предотвратить сохранение файла журнала графики в каталоге временных файлов, необходимо определить `DONT_SAVE_VSGLOG_TO_TEMP` перед включением `vsgcapture.h`.

## <a name="example"></a>Пример
 В этом примере показано, как сохранить файл журнала графики в абсолютный путь на главном компьютере.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>См. также
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
