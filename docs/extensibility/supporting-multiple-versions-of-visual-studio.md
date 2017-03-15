---
title: "Поддержка нескольких версий Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Поддержка нескольких версий Visual Studio"
  - "Пакеты VSPackage, side-by-side совместимости"
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Поддержка нескольких версий Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Термин *side\-by\-side* означает, что можно установить и поддерживать несколько версий продукта на одном компьютере. Для пакетов VSPackages, это означает, что у пользователя могут быть установлены на одном компьютере несколько версий Visual Studio. Тем не менее не может иметь версии side\-by\-side вашей VSPackages загружаются в одной версии Visual Studio.  
  
 Прежде чем вносить VSPackage могут быть загружены в side\-by\-side версий Visual Studio, необходимо учитывайте следующее:  
  
-   Необходимо определить, какие стратегии реализации side\-by\-side, необходимо следовать.  
  
     Дополнительные сведения см. в разделе [Выбор между VSPackages общих и управление версиями](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Форматы файлов вашего решения и проекта должны помещаться стратегии реализации.  
  
     Дополнительные сведения см. в разделах [Обновление пользовательских проектов](../misc/upgrading-custom-projects.md) и [Регистрация расширений файлов для развертываний Side\-By\-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Установщик должен обрабатывать стратегии реализации, чтобы версий компонентов, а также компоненты, совместно используется всеми версиями правильно установлены и зарегистрированы.  
  
     Дополнительные сведения см. в разделе [Установка пакетов VSPackages с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) а также [Компонент управления](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Чтобы установить версию Visual Studio также устанавливает соответствующую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Например, при установке Visual Studio 2010 и Visual Studio 2012 на одном компьютере также устанавливаются версии 4.0 и 4.5 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], соответственно.  
  
## В этом подразделе  
 [Выбор между VSPackages общих и управление версиями](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Способы устранения проблем side\-by\-side в VSPackage.  
  
 [Регистрация расширений файлов для развертываний Side\-By\-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Описывает, как в случае side\-by\-side VSPackage можно зарегистрировать сопоставления файлов.  
  
## Связанные подразделы  
 [Установка пакетов VSPackage](../misc/installing-vspackages.md)  
 Описывает способы создания и установки пакетов VSPackages и поддержки пользователей, работающих одновременно несколько версий Visual Studio.