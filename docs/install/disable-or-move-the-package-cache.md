---
title: Отключение или перемещение кэша пакетов
description: Сведения о включении, отключении и перемещении кэша пакетов для развертывания Visual Studio.
ms.date: 04/14/2017
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed8a827dd1edfcd2f0e61361ec4b20f6662ab036
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909024"
---
# <a name="disable-or-move-the-package-cache"></a>Отключение или перемещение кэша пакетов

Кэш пакетов служит источником для установленных пакетов на случай, если потребуется восстановить установку Visual Studio или других связанных продуктов без подключения к Интернету. Но в некоторых конфигурациях дисков или систем вы предпочтете не сохранять эти пакеты локально.
При необходимости их всегда можно скачать с помощью установщика, так что вы можете отключить или переместить кэш пакетов, чтобы сохранить или высвободить место на диске.

## <a name="disable-the-package-cache"></a>Отключение кэша пакетов

Прежде чем установить, изменить или восстановить Visual Studio или другие продукты с помощью нового установщика, вы можете запустить этот установщик с параметром `--nocache`.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Теперь любая операция, выполняемая для любого продукта, приведет к удалению всех существующих пакетов для этого продукта и пакеты не будут сохраняться после установки. Если в процессе изменения или восстановления Visual Studio потребуются какие-либо пакеты, они будут автоматически загружены, а затем удалены после установки.

Если вы захотите снова включить кэш, передайте установщику параметр `--cache`. В кэш включаются только те пакеты, которые нужны для установки. Если вы хотите восстановить все пакеты перед отключением от сети, выполните процедуру восстановления Visual Studio.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Также вы можете использовать `KeepDownloadedPayloads` [политики реестра](set-defaults-for-enterprise-deployments.md), чтобы отключить кэш перед установкой, изменением или восстановлением Visual Studio.

## <a name="move-the-package-cache"></a>Перемещение кэша пакетов

В типичной конфигурации операционная система Windows устанавливается на диске SSD, а более крупный диск HDD (или несколько дисков) отводятся под потребности среды разработки, например для хранения исходных кодов, двоичных файлов и других ресурсов. Если вы намерены работать в автономном режиме, кэш пакетов можно переместить в другое расположение.

В настоящее время для этого нужно применить `CachePath` [политику реестра](set-defaults-for-enterprise-deployments.md) перед установкой, изменением или восстановлением Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md)
* [Настройка параметров по умолчанию для корпоративного развертывания](set-defaults-for-enterprise-deployments.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
