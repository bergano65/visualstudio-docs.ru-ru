---
title: Отключение или перемещение кэша пакетов
description: Сведения о включении, отключении и перемещении кэша пакетов для развертывания Visual Studio.
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e328bf8420f9cc7cf207ede6b6447ed291b77745
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949458"
---
# <a name="disable-or-move-the-package-cache"></a>Отключение или перемещение кэша пакетов

Кэш пакетов служит источником для установленных пакетов на случай, если потребуется восстановить установку Visual Studio или других связанных продуктов без подключения к Интернету. Но в некоторых конфигурациях дисков или систем вы можете предпочесть не сохранять эти пакеты локально.
При необходимости их всегда можно скачать с помощью установщика, поэтому вы можете отключить или переместить кэш пакетов, чтобы сэкономить или освободить место на диске.

## <a name="disable-the-package-cache"></a>Отключение кэша пакетов

Прежде чем установить, изменить или восстановить Visual Studio или другие продукты с помощью нового установщика, вы можете запустить этот установщик с параметром `--nocache`.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Теперь любая операция, выполняемая для любого продукта, приведет к удалению всех существующих пакетов для этого продукта и пакеты не будут сохраняться после установки. Если в процессе изменения или восстановления Visual Studio потребуются какие-либо пакеты, они будут автоматически загружены, а затем удалены после установки.

Если вы захотите снова включить кэш, передайте установщику параметр `--cache`. В кэш включаются только те пакеты, которые нужны для установки. Если вы хотите восстановить все пакеты, перед отключением от сети выполните процедуру восстановления Visual Studio.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Вы также можете использовать [политики реестра](set-defaults-for-enterprise-deployments.md) `KeepDownloadedPayloads`, чтобы отключить кэш перед установкой, изменением или восстановлением Visual Studio.

## <a name="move-the-package-cache"></a>Перемещение кэша пакетов

В типичной конфигурации операционная система Windows устанавливается на диске SSD, а более крупный диск HDD (или несколько дисков) отводятся под потребности среды разработки, например для хранения исходных кодов, двоичных файлов и других ресурсов. Если вы намерены работать в автономном режиме, кэш пакетов можно переместить в другое расположение.

Сейчас для этого нужно применить [политику реестра](set-defaults-for-enterprise-deployments.md) `CachePath` перед установкой, изменением или восстановлением Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md)
* [Настройка параметров по умолчанию для корпоративного развертывания](set-defaults-for-enterprise-deployments.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
