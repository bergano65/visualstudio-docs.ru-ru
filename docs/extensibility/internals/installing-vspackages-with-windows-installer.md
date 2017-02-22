---
title: "Установка пакетов VSPackages с помощью установщика Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Установка [Visual Studio SDK] с помощью установщика Windows"
  - "Пакеты VSPackage, развертывание"
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# Установка пакетов VSPackages с помощью установщика Windows
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Интеграция ваше в VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] требуется больше, чем просто скопировать файлы на компьютер пользователя.  Установщик в VSPackage должен устанавливать VSPackage и ее зависимые файлы и регистр и объединить их в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  В VSPackage может воспользоваться преимуществами функции, как отображение значка на integration services [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] экран\-заставка и о диалоговом окне.  
  
 Файлы установщика Microsoft Windows рекомендуемый способ распределения ваше VSPackages.  Простые в использовании пакеты установщика Windows могут выполняться в любой операционной системе windows, поддерживаемой by [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Дополнительные сведения см. в разделе [Windows Installer](http://msdn.microsoft.com/ru-ru/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## В этом подразделе  
 [Основы установщика Windows](../../extensibility/internals/windows-installer-basics.md)  
 Общие сведения о установщика Windows.  
  
 [Сценарии установки VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Описывает различные способы поддержки параллельные установки и пользовательского VSPackages и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Создание пакета установщика Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Общие сведения о типичных действий установщики выполнить, чтобы правильно устанавливать и интегрировать VSPackages в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)  
 Описывает, как установщик может обнаружить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и его компонентов и отменять установку, если не выполняются требования к VSPackage.  
  
 [Компонент управления](../../extensibility/internals/component-management.md)  
 Содержит сведения о том, как начать установщика, который будет поддерживать целостность предыдущих версий продукта.  
  
 [Выбор каталога установки для VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Приведены параметры поиска VSPackages.  
  
 [Регистрация VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Обсуждается VSPackages регистрируется во время установки и почему собственн\-регистрация неверная идея.  
  
 [Развертывание типы проектов](../../extensibility/internals/deploying-project-types.md)  
 Обсуждается использование нового типа агрегатора проекта для типов проектов управляемого кода.  
  
 [Практическое руководство: создание сведения реестра для программы установки](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Объясняет, как использовать RegPkg.exe для создания манифеста регистрации для управляемого VSPackage.  
  
 [Команды, которые необходимо выполнить после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Объясняет, как интегрировать VSPackages в запуска команд после установки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [При удалении VSPackage с помощью установщика Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Описывает шаги в установщик должен выполняться, когда пользователи удалить в VSPackage.  
  
## Связанные подразделы  
 [Установка пакетов VSPackage](../../misc/installing-vspackages.md)  
 Обсуждается создание и установка VSPackages, а также поддерживать пользователи которых запустите несколько версий [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] одновременно.