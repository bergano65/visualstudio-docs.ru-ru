---
title: Настройка параметров по умолчанию для корпоративного развертывания
description: Сведения о доменных политиках и других операциях настройки для корпоративного развертывания Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8fd5e96246778e1a8fd4ec1d87221ff04e8647cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959276"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Настройка параметров по умолчанию для корпоративного развертывания Visual Studio

Вы можете задать политики реестра, влияющие на развертывание Visual Studio. Эти политики являются глобальными для нового установщика и изменяют следующие параметры:

- куда устанавливаются некоторые пакеты, используемые совместно с другими версиями или экземплярами;
- где кэшируются пакеты;
- все ли пакеты кэшируются.

Некоторые из этих политик вы можете задать с помощью [параметров командной строки](use-command-line-parameters-to-install-visual-studio.md), значений реестра на локальном компьютере или групповой политики для всей организации.

## <a name="registry-keys"></a>Разделы реестра

В нескольких местах можно настроить значения по умолчанию для предприятия, что позволит управлять ими через групповую политику или напрямую через реестр. Visual Studio последовательно осуществляет перебор этих мест для проверки установленных политик в указанном ниже порядке. Если значение политики будет обнаружено в любом из них, остальные значения игнорируются.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (на 64-разрядных операционных системах)

> [!IMPORTANT]
> Если вы не задаете раздел `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`, но вместо этого задаете один из других разделов, в 64-разрядных операционных системах необходимо задать оба других раздела. Эта проблема будет устранена в будущих обновлениях продукта.

Некоторые параметры реестра устанавливаются автоматически при первом использовании, если они не были настроены ранее. Это гарантирует, что при последующих установках будут использоваться такие же значения. Они хранятся в втором разделе реестра, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Вы можете задать указанные ниже значения реестра.

| **Название** | **Тип** | **Default** | **Описание** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` либо `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Каталог, где хранятся манифесты пакетов и полезные данные (необязательно). Дополнительные сведения см. в статье об [отключении или перемещении кэша пакетов](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Сохранение полезных данных пакетов даже после их установки. Это значение можно изменить в любое время. После отключения этой политики удаляются все кэшированные полезные данные пакетов для экземпляров, которые вы восстанавливаете или изменяете. Дополнительные сведения см. в статье об [отключении или перемещении кэша пакетов](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` либо `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Каталог, в котором устанавливаются некоторые пакеты, используемые совместно несколькими версиями экземпляров Visual Studio. Это значение можно изменить в любое время, но все изменения повлияют только на будущие установки. Все уже установленные продукты необходимо оставить на прежних местах, так как при перемещении они могут работать неправильно. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Программа установки не может автоматически скачивать обновления для всех установленных продуктов Visual Studio. Это значение можно изменить в любое время. |

> [!IMPORTANT]
> Если вы измените политику реестра `CachePath` после любой установки, необходимо перенести существующий кэш пакетов в новое расположение и проверить его защиту, чтобы `SYSTEM` и `Administrators` имели полный доступ, а `Everyone` — доступ на чтение.
> Если кэш не будет перенесен или правильно защищен, при последующих установках могут возникнуть проблемы.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также раздел

- [Установка Visual Studio](install-visual-studio.md)
- [Отключение или перемещение кэша пакетов](disable-or-move-the-package-cache.md)
- [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
