---
title: Поддержка нескольких версий Visual Studio 2015 | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a4ad8b128ea614ba60a19c3526d20af80aab937
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992069"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Поддержка нескольких версий Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Термин *side-by-side* означает, что можно установить и поддерживать несколько версий продукта на одном компьютере. Для пакетов VSPackage, это означает, что пользователь может иметь несколько версий Visual Studio, которые установлены на одном компьютере. Тем не менее не может иметь side-by-side версиях пакетов VSPackage загружается одна версия Visual Studio.

 Прежде чем вносить VSPackage может быть загружена в side-by-side версиях Visual Studio, необходимо учитывайте следующее:

-   Необходимо определить, какая стратегия реализации side-by-side, необходимо следовать.

     Дополнительные сведения см. в разделе [Выбор между общими и с контролем версий пакетов VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

-   Форматы файлов вашего решения и проекта должны умещаться стратегии реализации.

     Дополнительные сведения см. в разделе [обновление пользовательских проектов](../misc/upgrading-custom-projects.md) и [Регистрация расширений имен файлов для развертываний Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

-   Установщик должен обрабатывать стратегии реализации, чтобы версий компонентов, а также компоненты, общие для всех версий правильно установлен и зарегистрирован.

     Дополнительные сведения см. в разделе [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) , а также [Управление компонентами](../extensibility/internals/component-management.md).

    > [!NOTE]
    >  Установка версии Visual Studio также устанавливает соответствующую версию [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Например, при установке Visual Studio 2010 и Visual Studio 2012 на одном компьютере также устанавливается версии 4.0 и 4.5 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], соответственно.

## <a name="in-this-section"></a>В этом разделе
 [Выбор между общими и с контролем версий пакетов VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md) объясняется, как устранить проблемы с side-by-side в VSPackage.

 [Регистрация расширений имен файлов для развертываний Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) описывает, как VSPackage может зарегистрировать сопоставлений файлов в сценарии side-by-side.

## <a name="related-sections"></a>Связанные разделы
 [Установка пакетов VSPackage](../misc/installing-vspackages.md) описывается, как выполнить сборку и установку пакетов VSPackage и как поддержать пользователей, выполняющих несколько версий Visual Studio, в то же время.
