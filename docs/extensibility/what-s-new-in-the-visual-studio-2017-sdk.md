---
title: Что&#39;нового в Визуальной студии 2017 SDK Документы Майкрософт
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697200"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Что&#39;нового в визуальной студии 2017 SDK

Визуальная студия SDK имеет следующие новые и обновленные функции для Visual Studio 2017.

## <a name="vsix-v3-format"></a>Формат VSIX v3

Для поддержки новой легкой установки Visual Studio 2017, формат манифеста расширения VSIX был обновлен до версии 3 (VSIX v3).

Новый формат имеет поддержку:

* Явно декларирование предпосылок, которые должны быть обнаружены и установлены VSIXInstaller.
* Сборки Ngen на установке расширения.
* Установка активов за пределами обычного корневия расширения.

Чтобы узнать об этих изменениях, смотрите следующие темы:

* [Изменения в расширяемости для Visual Studio 2017](breaking-changes-2017.md)
* [Поддержка NGen в VSIX v3](ngen-support.md)
* [Установка за пределами папки расширений](set-install-root.md)
* [Часто задаваемые вопросы для визуальной студии 2017 расширяемость](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Проект миграции в Visual Studio 2017

Чтобы узнать, как обновить ваши проекты расширяемости и их VSIX манифесты Visual Studio 2017, смотрите [Как: Миграция расширяемость проектов Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Пользовательские шаблоны проектов и элементов

Начиная с Visual Studio 2017, сканирование пользовательских шаблонов проектов и элементов больше не будет выполняться. Вместо этого расширение должно предоставить файлы манифеста шаблонов, описывающие расположение этих шаблонов. Вы можете использовать Visual Studio 2017 для обновления расширений VSIX. При развертывании расширения с помощью MSI необходимо создавать файлы манифеста шаблона вручную. Для получения дополнительной [Upgrade custom project and item templates for Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)информации см. Схема манифеста шаблона задокументирована в [ссылке на схему Visual Studio.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="updated-extension-performance-guidelines"></a>Обновленные руководящие принципы производительности расширения

Существует новая статья [Как: Диагностика производительности расширения](how-to-diagnose-extension-performance.md) статьи [под Управление VSPackages,](managing-vspackages.md) чтобы показать, как обнаружить и проанализировать влияние расширения на Visual Studio запуска и времени загрузки решения.
