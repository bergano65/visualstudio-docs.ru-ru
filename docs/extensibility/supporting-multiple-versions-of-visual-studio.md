---
title: Поддержка нескольких версий Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db820ba35f53366aa6a8e4f88d758ade97b44bd7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026870"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Поддержка нескольких версий Visual Studio
Термин *side-by-side* означает, что можно установить и поддерживать несколько версий продукта на одном компьютере. Для пакетов VSPackage, это означает, что пользователь может иметь несколько версий Visual Studio, которые установлены на одном компьютере. Тем не менее не может иметь side-by-side версиях пакетов VSPackage загружается одна версия Visual Studio.  
  
 Прежде чем вносить VSPackage может быть загружена в side-by-side версиях Visual Studio, необходимо учитывайте следующее:  
  
- Необходимо определить, какая стратегия реализации side-by-side, необходимо следовать.  
  
   Дополнительные сведения см. в разделе [Выбор между общими и с контролем версий пакетов VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
- Форматы файлов вашего решения и проекта должны умещаться стратегии реализации.  
  
   Дополнительные сведения см. в разделе [обновление пользовательских проектов](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) и [Регистрация расширений имен файлов для развертываний Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Установщик должен обрабатывать стратегии реализации, чтобы версий компонентов, а также компоненты, общие для всех версий правильно установлен и зарегистрирован.  
  
   Дополнительные сведения см. в разделе [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) , а также [Управление компонентами](../extensibility/internals/component-management.md).  
  
  > [!NOTE]
  >  Установка версии Visual Studio также устанавливает соответствующую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Например, при установке Visual Studio 2010 и Visual Studio 2012 на одном компьютере также устанавливается версии 4.0 и 4.5 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], соответственно.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Выбор между общими пакетами VSPackage и пакетами с контролем версий](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Объясняется, как устранить проблемы с side-by-side в VSPackage.  
  
 [Регистрация расширений имен файлов для параллельных развертываний](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Описывает, как VSPackage может зарегистрировать сопоставлений файлов в сценарии side-by-side.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
