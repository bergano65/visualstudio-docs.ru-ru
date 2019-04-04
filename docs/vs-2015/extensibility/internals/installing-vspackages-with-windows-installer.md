---
title: Установка пакетов VSPackage с помощью установщика Windows | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d5b22479996bca6ee69c1334d79f012024b865d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991518"
---
# <a name="installing-vspackages-with-windows-installer"></a>Установка пакетов VSPackage с помощью установщика Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Интеграция пакета VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] требует не только копирование файлов на компьютере пользователя. Установщик вашего VSPackage необходимо установить VSPackage и его зависимых файлов и зарегистрировать, так и их интеграция в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. VSPackage может воспользоваться преимуществами функций интеграции, такие как отображение значка на [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -заставка экрана и диалогового окна About.  
  
 Файлы установщика Microsoft Windows являются рекомендуемым способом распространения пакетов VSPackage. Пакеты установщика Windows для использования можно запустить в любой операционной системе Windows, поддерживаемых [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [установщика Windows](http://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Основные сведения об установщике Windows](../../extensibility/internals/windows-installer-basics.md)  
 Обзор установщика Windows.  
  
 [Сценарии установки VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Описаны различные возможности, которые может поддерживать side-by-side установки обоих пакетов VSPackage и [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Создание пакета установщика Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Общие сведения о типичные действия, выполните установщики правильно установить и интегрировать пакетов VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)  
 Описывает, как можно обнаружить установщик [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и его компоненты и Отмена установки, если не выполняются требования к VSPackage.  
  
 [Управление компонентами](../../extensibility/internals/component-management.md)  
 Описываются способы разработки установщик, который будет поддерживать целостность данных в предыдущих версиях продукта.  
  
 [Выбор каталога установки для VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Перечислены варианты для поиска пакетов VSPackage.  
  
 [Регистрация VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Описывает, как пакеты VSPackage регистрируются во время установки и почему самостоятельной регистрации не рекомендуется.  
  
 [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)  
 В этой статье описывается использование средства инвентаризации программного обеспечения новый тип проекта для типов проектов управляемого кода.  
  
 [Практическое руководство. Создание сведений реестра для установщика](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 В этой статье описывается использование RegPkg.exe для создания манифеста регистрации для управляемого пакета VSPackage.  
  
 [Команды, которые необходимо выполнить после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Объясняет, как для выполнения команд после установки для интеграции пакетов VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Удаление пакета VSPackage с помощью установщика Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Описывает шаги, которые установщик необходимо выполнить, если пользователи удалили VSPackage.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Установка пакетов VSPackage](../../misc/installing-vspackages.md)  
 Описывается, как выполнить сборку и установку пакетов VSPackage и как поддержать пользователей, выполняющих несколько версий из [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в то же время.
