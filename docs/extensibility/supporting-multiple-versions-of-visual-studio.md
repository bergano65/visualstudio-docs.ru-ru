---
title: Поддержка нескольких версий визуальной студии (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699477"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Поддержка нескольких версий Visual Studio
Термин *«бок о бок»* означает, что вы можете установить и поддерживать несколько версий продукта на одном компьютере. Для VSPackages это означает, что пользователь может иметь несколько версий Visual Studio, установленных на одном компьютере. Тем не менее, вы не можете иметь бок о бок версии вашего VSPackages загружены в одной версии Visual Studio.

 Прежде чем сделать ваш VSPackage в состоянии быть загружены в бок о бок версии Visual Studio, рассмотрим следующее:

- Необходимо определить, какой стратегии реализации вы хотите следовать.

   Для получения дополнительной информации [см.](../extensibility/choosing-between-shared-and-versioned-vspackages.md)

- Форматы файлов решения и файла проекта должны соответствовать вашей стратегии реализации.

   Для получения дополнительной информации [Registering File Name Extensions for Side-By-Side Deployments](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) [см.](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)

- Установщик должен обрабатывать стратегию реализации, чтобы компоненты, версированные, а также компоненты, общие для всех версий, были правильно установлены и зарегистрированы.

   Для получения дополнительной информации, см [Установка VSPackages с установкой Windows,](../extensibility/internals/installing-vspackages-with-windows-installer.md) а также [управление компонентами](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Установка версии Visual Studio также устанавливает соответствующую версию рамочного .NET. Например, установка Visual Studio 2010 и Visual Studio 2012 на том же компьютере также устанавливает версии 4.0 и 4.5 из .NET Framework, соответственно.

## <a name="in-this-section"></a>В этом разделе
- [Выбор между общими и версиями VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Объясняет, как решить проблемы, связанные с бок о бок в вашем VSPackage.

- [Регистрация расширений имен файлов для боковых развертываний](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Описывает, как ваш VSPackage может регистрировать ассоциации файлов в сценарии.

## <a name="related-sections"></a>Связанные разделы
- [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
