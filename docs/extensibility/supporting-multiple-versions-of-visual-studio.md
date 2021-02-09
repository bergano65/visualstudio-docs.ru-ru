---
title: Поддержка нескольких версий Visual Studio | Документация Майкрософт
description: Узнайте, как можно поддерживать несколько версий Visual Studio, с которыми пакеты VSPackage могут загружаться в разные версии.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52b8bf1be57e10790d91d4712e56d707621cc7df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889945"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Поддержка нескольких версий Visual Studio
Термин " *параллельно* " означает, что можно установить и поддерживать несколько версий продукта на одном компьютере. Для пакетов VSPackage это означает, что на одном компьютере может быть установлено несколько версий Visual Studio. Однако параллельные версии пакетов VSPackage не могут быть загружены в одну версию Visual Studio.

 Перед тем как сделать пакет VSPackage загруженным в параллельные версии Visual Studio, учитывайте следующие возможности.

- Необходимо определить стратегию параллельной реализации, которую вы хотите соблюдать.

   Дополнительные сведения см. в статье [Выбор между общими и версиями пакетов VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Форматы файлов вашего решения и проекта должны соответствовать вашей стратегии реализации.

   Дополнительные сведения см. в статьях [Обновление пользовательских проектов](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) и [Регистрация расширений имен файлов для параллельных развертываний](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Установщик должен реализовать стратегию реализации, чтобы компоненты с управлением версиями, а также компоненты, общие для всех версий, были правильно установлены и зарегистрированы.

   Дополнительные сведения см. [в разделе Установка пакетов VSPackage с помощью установщик Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) , а также [Управление компонентами](../extensibility/internals/component-management.md).

  > [!NOTE]
  > При установке версии Visual Studio также устанавливается соответствующая версия платформа .NET Framework. Например, при установке Visual Studio 2010 и Visual Studio 2012 на одном компьютере также устанавливаются версии 4,0 и 4,5 платформа .NET Framework соответственно.

## <a name="in-this-section"></a>В этом разделе
- [Выбор между общими и версиями пакетов VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Описание способов устранения проблем, связанных с параллельным выполнением пакета VSPackage.

- [Регистрация расширений имен файлов для параллельных развертываний](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Описывает, как VSPackage может регистрировать сопоставления файлов в параллельном сценарии.

## <a name="related-sections"></a>Связанные разделы
- [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
