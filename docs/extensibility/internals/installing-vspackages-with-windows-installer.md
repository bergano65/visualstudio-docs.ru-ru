---
title: Установка пакетов VSPackage с помощью установщика Windows | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6fafebe0dc2bb8e13c99be8b340e7f5663a9930f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131012"
---
# <a name="installing-vspackages-with-windows-installer"></a>Установка пакетов VSPackage с помощью установщика Windows
Интеграции VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] требуется больше, чем просто копирование файлов на компьютере пользователя. Установщик вашего VSPackage необходимо установить пакет VSPackage и его зависимых файлов, регистрацию и интегрировать их в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. VSPackage может воспользоваться преимуществами функций интеграции, например, отображение значка на [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -заставка экрана и о диалоговое окно.  
  
 Файлы установщика Windows, рекомендуемый способ распространения пакетов VSPackage. Для использования пакетов установщика Windows можно запустить в любой операционной системе Windows, поддерживаемых [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [установщика Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Основные сведения об установщике Windows](../../extensibility/internals/windows-installer-basics.md)  
 Обзор установщика Windows.  
  
 [Сценарии установки VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Описывает различные способы, может поддерживать side-by-side установок обоих пакетов VSPackage и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Создание пакета установщика Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Общие сведения о типичные действия, выполните установщики для правильной установки и интеграции пакетов VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)  
 Описывает, каким образом можно определить установщика [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и его компоненты и отмены установки, если не выполняются требования к VSPackage.  
  
 [Управление компонентами](../../extensibility/internals/component-management.md)  
 В этом разделе рассматривается разработка установщик, который будет поддерживать целостность предыдущих версий продукта.  
  
 [Выбор каталога установки для VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Итоги по параметрам, ищите пакеты VSPackage.  
  
 [Регистрация VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Описывает, как пакеты VSPackage регистрируются во время установки и почему саморегистрацию не рекомендуется.  
  
 [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)  
 Описываются способы использования новому средству тип проекта для типов управляемых проектов.  
  
 [Практическое руководство. Создание сведений реестра для установщика](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Описание способов использования RegPkg.exe для создания манифеста регистрации для управляемого пакета VSPackage.  
  
 [Команды, которые необходимо выполнить после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Описание способов выполнения команды после установки для интеграции пакетов VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Удаление пакета VSPackage с помощью установщика Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Описание действий установщика необходимо выполнить, если пользователи удалили VSPackage.  