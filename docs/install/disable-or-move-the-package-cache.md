---
title: "Отключение или перемещение кэша пакетов | Документация Майкрософт"
description: "Включение, отключение и перемещение кэша пакетов для развертывания Visual Studio."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: heaths
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: e07f1c04d9695e092db7aa29e641ce9bd36250f9
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

---
# <a name="disable-or-move-the-package-cache"></a>Отключение или перемещение кэша пакетов

Кэш пакетов служит источником для установленных пакетов на случай, если потребуется восстановить установку Visual Studio или других связанных продуктов без подключения к Интернету. Но в некоторых конфигурациях дисков или систем вы предпочтете не сохранять эти пакеты локально.
При необходимости их всегда можно скачать с помощью установщика, так что вы можете отключить или переместить кэш пакетов, чтобы сохранить или высвободить место на диске.

## <a name="disable-the-package-cache"></a>Отключение кэша пакетов

Прежде чем установить, изменить или восстановить Visual Studio или другие продукты с помощью нового установщика, вы можете запустить этот установщик с параметром `--nocache`.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Теперь любая операция, выполняемая для любого продукта, приведет к удалению всех существующих пакетов для этого продукта и пакеты не будут сохраняться после установки. Если в процессе изменения или восстановления Visual Studio потребуются какие-либо пакеты, они будут автоматически загружены, а затем удалены после установки.

Если вы захотите снова включить кэш, передайте установщику параметр `--cache`. В кэш включаются только те пакеты, которые нужны для установки. Если вы хотите восстановить все пакеты перед отключением от сети, выполните процедуру восстановления Visual Studio.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Также вы можете использовать `KeepDownloadedPayloads` [политики реестра](set-defaults-for-enterprise-deployments.md), чтобы отключить кэш перед установкой, изменением или восстановлением Visual Studio.

## <a name="move-the-package-cache"></a>Перемещение кэша пакетов

В типичной конфигурации операционная система Windows устанавливается на диске SSD, а более крупный диск HDD (или несколько дисков) отводятся под потребности среды разработки, например для хранения исходных кодов, двоичных файлов и других ресурсов. Если вы намерены работать в автономном режиме, кэш пакетов можно переместить в другое расположение.

В настоящее время для этого нужно применить `CachePath` [политику реестра](set-defaults-for-enterprise-deployments.md) перед установкой, изменением или восстановлением Visual Studio.

## <a name="see-also"></a>См. также

 * [Установка Visual Studio](install-visual-studio.md)
 * [Настройка параметров по умолчанию для корпоративного развертывания](set-defaults-for-enterprise-deployments.md)
 * [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Сообщение о проблеме с Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

