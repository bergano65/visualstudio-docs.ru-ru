---
title: Установка пакетов VSPackage с помощью установщика Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cd5f25e1e87ba3db360b328b4f5a245697cba45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860285"
---
# <a name="installing-vspackages-with-windows-installer"></a>Установка пакетов VSPackage с помощью установщика Windows
Интеграция пакета VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] требует не только копирование файлов на компьютере пользователя. Установщик вашего VSPackage необходимо установить VSPackage и его зависимых файлов и зарегистрировать, так и их интеграция в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. VSPackage может воспользоваться преимуществами функций интеграции, такие как отображение значка на [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -заставка экрана и диалогового окна About.

 Файлы установщика Microsoft Windows являются рекомендуемым способом распространения пакетов VSPackage. Пакеты установщика Windows для использования можно запустить в любой операционной системе Windows, поддерживаемых [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [установщика Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).

## <a name="in-this-section"></a>В этом разделе
- [Основные сведения об установщике Windows](../../extensibility/internals/windows-installer-basics.md)

 Обзор установщика Windows.

- [Сценарии установки VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Описаны различные возможности, которые может поддерживать side-by-side установки обоих пакетов VSPackage и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Создание пакета установщика Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Общие сведения о типичные действия, выполните установщики правильно установить и интегрировать пакетов VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)

 Описывает, как можно обнаружить установщик [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и его компоненты и Отмена установки, если не выполняются требования к VSPackage.

- [Управление компонентами](../../extensibility/internals/component-management.md)

 Описываются способы разработки установщик, который будет поддерживать целостность данных в предыдущих версиях продукта.

- [Выбор каталога установки для VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Перечислены варианты для поиска пакетов VSPackage.

- [Регистрация VSPackage](../../extensibility/internals/vspackage-registration.md)

 Описывает, как пакеты VSPackage регистрируются во время установки и почему самостоятельной регистрации не рекомендуется.

- [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)

 В этой статье описывается использование средства инвентаризации программного обеспечения новый тип проекта для типов проектов управляемого кода.

- [Практическое руководство. Создание сведений реестра для установщика](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 В этой статье описывается использование RegPkg.exe для создания манифеста регистрации для управляемого пакета VSPackage.

- [Команды, которые необходимо выполнить после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Объясняет, как для выполнения команд после установки для интеграции пакетов VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Удаление пакета VSPackage с помощью установщика Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Описывает шаги, которые установщик необходимо выполнить, если пользователи удалили VSPackage.