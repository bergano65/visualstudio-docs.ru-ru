---
title: Изменение полезных данных пакета после выпуска
description: Сведения о том, как при создании макета определить, изменены ли полезные данные пакетов после отправки выпуска.
ms.date: 05/22/2019
ms.topic: conceptual
author: et13
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6a4eb286344b6dce7a4814089db013965eb34c98
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402264"
---
# <a name="package-payload-changes"></a>Изменения полезных данных пакета

Некоторые полезные данные пакетов можно изменить после отправки выпуска. Это может привести к изменению содержимого макета, в зависимости от того, когда пользователь создал его.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Проверка наличия в макете последних изменений полезных данных пакета

Вот как можно определить, получил ли созданный ранее макет полезные данные пакета, которые были изменены после отправки выпуска:

1. Откройте журнал установки. Журнал обычно находится в расположении `%TEMP%\dd_setup_[date].log`, где `[date]` обозначает дату начала создания макета, представленную в формате `yyyyMMddHHmmss`.

2. В журнале найдите строку с такой же структурой, как у следующего текста:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Затем найдите в журнале строки, которые свидетельствуют об успешном скачивании для [path]. Они могут выглядеть примерно так:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>См. также

* [Создание сетевой установки Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md)