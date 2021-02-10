---
title: DONT_SAVE_VSGLOG_TO_TEMP | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f94b287f6ed9d4cda0696252ba32d493879ed5c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880272"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Определяет своим наличием, нужно ли сохранять файл журнала графики в каталог временных файлов пользователя.

## <a name="syntax"></a>Синтаксис

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Значение
 Символ препроцессора, который имеет наличие или отсутствие определяет, нужно ли сохранять файл журнала графики в каталог временных файлов пользователя. Если этот символ препроцессора определен, имя файла является определенным `VSG_DEFAULT_RUN_FILENAME` относительно текущего каталога захватываемого приложения или представляет собой абсолютный путь; в противном случае это имя, определенное `VSG_DEFAULT_RUN_FILENAME` относительно каталогу временных файлов пользователя, которое не может быть абсолютным путем.

## <a name="remarks"></a>Примечания
 В зависимости от привилегий пользователя файл журнала графики может быть запрещено сохранять в произвольном месте. Мы рекомендуем сохранять графические журналы в каталог временных файлов пользователя или в другое известное место, если вы не уверены, сможет ли пользователь записать данные в выбранное вами место.

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
