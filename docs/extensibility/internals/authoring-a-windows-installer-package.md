---
title: Авторство пакета установки Windows (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710029"
---
# <a name="author-a-windows-installer-package"></a>Автор пакета установки Windows
Данные диски модели установки Windows. Например, вместо того, чтобы писать процедурный скрипт для копирования файлов и записи записей в реестре, вы авторьтесь строк и столбцов в таблицах баз данных, содержащих данные файлов и реестров.

## <a name="database-entries"></a>Записи баз данных
Для установки VSPackage пакет установки Windows должен содержать записи баз данных для выполнения следующих задач:

- Поиск в системе, чтобы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] найти версии ваших поддержки VSPackage (с помощью таблиц установки Windows, которые включают AppSearch, CompLocator, RegLocator, DrLocator и подпись).

- Отмените установку, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] если не установлена поддерживаемая версия или если не выполнено другое системное требование VSPackage (с помощью таблицы LaunchCondition).

- Установите VSPackage и зависимые файлы (с использованием таблиц каталога, компонентов и файлов).

- Добавить соответствующую информацию для VSPackage в реестр (с помощью таблицы реестра).

- Интегрируйте VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] позвонив **по devenv.exe/setup** (с помощью таблицы CustomAction).

Для получения дополнительной [Windows Installer](/windows/desktop/Msi/windows-installer-portal)информации см.

## <a name="setup-tools"></a>Инструменты настройки
Различные сторонние средства настройки обеспечивают среду разработки пакетов Windows Installer. Доступны следующие бесплатные инструменты:

- InstallShield ограниченным тиражом

   Вы можете получить ограниченную версию InstallShield через visual Studio Новый диалог **проекта.** Расширьте **другие типы проектов,** а затем выберите **настройку и развертывание.** Выберите шаблон InstallShield.

- Набор инструментов установки Windows XML

   Набор инструментов Windows Installer XML (WiX) создает пакеты Windows Installer из исходных файлов XML. Набор инструментов WiX — это проект с открытым исходным кодом Майкрософт. Вы можете скачать исходный код и исполняемые данные из [набора инструментов Wix.](https://sourceforge.net/projects/wix/)

   Для коммерческих продуктов, которые интегрируются в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], см. [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="see-also"></a>См. также
- [Установка VSPackages с установкой Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
