---
title: Установка VSPackages с установкой Windows (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707464"
---
# <a name="installing-vspackages-with-windows-installer"></a>Установка пакетов VSPackage с помощью установщика Windows
Интеграция VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в требует большего, чем просто копирование файлов на компьютер пользователя. Установщик VSPackage должен установить VSPackage и его зависимые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]файлы, а также зарегистрировать и интегрировать их в. Ваш VSPackage может воспользоваться функциями интеграции, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] такими как отображение значка на экране всплеска и о диалоговом поле.

 Файлы Microsoft Windows Installer являются рекомендуемым способом распространения VSPackages. Простые в использовании пакеты установки Windows могут работать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]на любой операционной системе Windows, поддерживаемой. Для получения дополнительной [Windows Installer](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)информации см.

## <a name="in-this-section"></a>В этом разделе
- [Основные сведения об установщике Windows](../../extensibility/internals/windows-installer-basics.md)

 Предоставляет обзор установки Windows.

- [Сценарии установки VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Обсуждается различные способы поддержки бок о бок установки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]как ваших VSPackages и .

- [Создание пакета установщика Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Обеспечивает обзор типичных шагов установщики следовать правильно установить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]и интегрировать VSPackages в .

- [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)

 Описывает, как установщик может обнаружить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и его компоненты и отменить настройку, если требования VSPackage не выполнены.

- [Управление компонентами](../../extensibility/internals/component-management.md)

 Обсуждает, как разработать установщик, который будет поддерживать целостность предыдущих версий продукта.

- [Выбор каталога установки для VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Обобщает варианты размещения VSPackages.

- [Регистрация VSPackage](../../extensibility/internals/vspackage-registration.md)

 Обсуждает, как VSPackages регистрируются во время установки и почему саморегистрация является плохой идеей.

- [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)

 Обсуждается, как использовать новый агрегатор проектного типа для типов управляемых кодов.

- [Практическое руководство. Создание сведений реестра для установщика](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Объясняет, как использовать RegPkg.exe для создания регистрационного манифеста для управляемого VSPackage.

- [Команды, которые необходимо выполнить после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Объясняет, как запустить пост-установку команд для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]интеграции VSPackages в .

- [Удаление пакета VSPackage с помощью установщика Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Описывает шаги, которые должен выполнять установщик, когда пользователи удалят ваш VSPackage.
