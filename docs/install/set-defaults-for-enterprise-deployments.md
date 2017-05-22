---
title: "Настройка параметров по умолчанию для корпоративного развертывания Visual Studio | Документация Майкрософт"
description: "Доменные политики и другие операции настройки для корпоративного развертывания Visual Studio."
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
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
ms.sourcegitcommit: 8f38b2707376d4bee8852ad107980fa925114d99
ms.openlocfilehash: 05c5fd9e4be4cbf7d40e27c7c97793bc2466efe3
ms.contentlocale: ru-ru
ms.lasthandoff: 05/05/2017

---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Настройка параметров по умолчанию для корпоративного развертывания Visual Studio

Вы можете задать политики реестра, влияющие на развертывание Visual Studio. Эти политики являются глобальными для нового установщика и изменяют следующие параметры:

- куда устанавливаются некоторые пакеты, используемые совместно с другими версиями или экземплярами;
- где кэшируются пакеты;
- все ли пакеты кэшируются.

Некоторые из этих политик вы можете задать с помощью [параметров командной строки](use-command-line-parameters-to-install-visual-studio.md), значений реестра на локальном компьютере или групповой политики для всей организации.

## <a name="registry-keys"></a>разделы реестра;

В нескольких местах можно настроить значения по умолчанию для предприятия, что позволит управлять ими через групповую политику или напрямую через реестр. Visual Studio последовательно осуществляет перебор этих мест для проверки установленных политик в указанном ниже порядке. Если значение политики будет обнаружено в любом из них, остальные значения игнорируются.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (на 64-разрядных операционных системах)

Некоторые значения реестра устанавливаются автоматически при первом использовании, если они не были настроены ранее. Это гарантирует, что при последующих установках будут использоваться такие же значения. Они хранятся в втором разделе реестра, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Вы можете задать следующие значения реестра.

| **Name** | **Type** | **Default** | **Описание** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` или `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Каталог, где хранятся манифесты пакетов и полезные данные (необязательно). Дополнительные сведения см. в статье об [отключении или перемещении кэша пакетов](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Сохранение полезных данных пакетов даже после их установки. Это значение можно изменить в любое время. После отключения этой политики удаляются все кэшированные полезные данные пакетов для экземпляров, которые вы восстанавливаете или изменяете. Дополнительные сведения см. в статье об [отключении или перемещении кэша пакетов](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` или `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Каталог, в котором устанавливаются некоторые пакеты, используемые совместно несколькими версиями экземпляров Visual Studio. Это значение можно изменить в любое время, но все изменения повлияют только на будущие установки. Все уже установленные продукты следует оставить на прежних местах, поскольку при перемещении они могут работать неправильно. |

> [!IMPORTANT]
> Если вы измените политику реестра `CachePath` после любой установки, необходимо перенести существующий кэш пакетов в новое расположение и проверить его защиту, чтобы `SYSTEM` и `Administrators` имели полный доступ, а `Everyone` — доступ на чтение.
> Если кэш не будет перенесен или правильно защищен, при последующих установках могут возникнуть проблемы.

## <a name="see-also"></a>См. также

 * [Установка Visual Studio](install-visual-studio.md)
 * [Отключение или перемещение кэша пакетов](disable-or-move-the-package-cache.md)
 * [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Сообщение о проблеме с Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

