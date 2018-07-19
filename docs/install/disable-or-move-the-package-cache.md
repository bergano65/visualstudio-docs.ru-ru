---
title: Отключение или перемещение кэша пакетов | Документация Майкрософт
description: Сведения о включении, отключении и перемещении кэша пакетов для развертывания Visual Studio.
ms.date: 04/14/2017
ms.technology: vs-acquisition
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
ms.openlocfilehash: 9c8d5ddfdc521e2c383f5f67a31f42f70f528161
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282685"
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

## <a name="get-support"></a>Техническая поддержка

Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:

* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем и искать решения в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/).
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio). (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md)
* [Настройка параметров по умолчанию для корпоративного развертывания](set-defaults-for-enterprise-deployments.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
