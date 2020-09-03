---
title: Установка пакетов VSPackage с помощью установщик Windows | Документация Майкрософт
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
ms.openlocfilehash: 35942f6babf18967e11f268ef0412acb4cc8edf7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687469"
---
# <a name="installing-vspackages-with-windows-installer"></a>Установка пакетов VSPackage с помощью установщика Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Интеграция пакета VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] требует больше, чем просто копирование файлов на компьютер пользователя. Установщик VSPackage должен установить пакет VSPackage и зависимые от него файлы, а также зарегистрировать и интегрировать их в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Пакет VSPackage может использовать преимущества функций интеграции, таких как отображение значка на [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] экране-заставке и диалоговом окне о программе.  
  
 Файлы Microsoft установщик Windows являются рекомендуемым способом распространения пакетов VSPackage. Простые в использовании пакеты установщик Windows могут работать в любой операционной системе Windows, поддерживаемой [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Дополнительные сведения см. в разделе [установщик Windows](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Основные сведения об установщике Windows](../../extensibility/internals/windows-installer-basics.md)  
 Содержит общие сведения о установщик Windows.  
  
 [Сценарии установки VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Обсуждаются различные способы поддержки параллельной установки как пакетов VSPackage, так и [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Создание пакета установщика Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Общие сведения о стандартных шагах установки, которые следует выполнить для правильной установки и интеграции пакетов VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)  
 Описывает, как установщик может обнаружить [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и его компоненты, и отменить установку, если требования VSPackage не выполнены.  
  
 [Управление компонентами](../../extensibility/internals/component-management.md)  
 Описывает, как разработать установщик, который будет поддерживать целостность предыдущих версий продукта.  
  
 [Выбор каталога установки для VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Содержит сводку параметров для поиска пакетов VSPackage.  
  
 [Регистрация VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Описывает, как пакеты VSPackage регистрируются во время установки и почему самостоятельная регистрация является неправильной идеей.  
  
 [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)  
 Описывает, как использовать новый агрегатор типа проекта для типов проектов управляемого кода.  
  
 [Практическое руководство. Создание сведений реестра для установщика](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Объясняется, как использовать RegPkg.exe для создания манифеста регистрации для управляемого пакета VSPackage.  
  
 [Команды, которые необходимо выполнить после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Объясняет, как выполнять команды после установки для интеграции пакетов VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Удаление пакета VSPackage с помощью установщика Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Описание шагов, которые должен выполнить установщик при удалении пакета VSPackage.  
  
## <a name="related-sections"></a>См. также  
 [Установка пакетов VSPackage](../../misc/installing-vspackages.md)  
 Описывает, как создавать и устанавливать пакеты VSPackage и как поддерживать пользователей, одновременно работающих с несколькими версиями [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
