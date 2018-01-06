---
title: "Какой &#39; новые возможности Visual Studio SDK 2017 г. | Документы Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f6b27e60f1cc47b236ed2d3516313537a6121be5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Какой &#39; новые возможности Visual Studio SDK 2017 г.

Пакет SDK для Visual Studio имеет следующие новые и обновленные средства для Visual Studio 2017 г.

## <a name="vsix-v3-format"></a>Формат VSIX v3

Для поддержки новой упрощенная установки Visual Studio 2017 г., формат манифеста расширения VSIX обновлена до версии 3 (VSIX v3).

Новый формат имеет поддержку:

* Явно объявив необходимые условия для выявления и установленные VSIXInstaller.
* Ngen'ing сборки при установке расширения.
* Установка средств за пределами корневого обычные расширения.

Дополнительные сведения об этих изменениях, см. в следующих разделах:

* [Изменения расширяемости для 2017 г.](breaking-changes-2017.md)
* [Поддержка NGen в VSIX v3](ngen-support.md)
* [Установка за пределами папки расширений](set-install-root.md)
* [Вопросы и ответы для расширяемости Visual Studio 2017 г.](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Перенос проекта расширения для Visual Studio 2017 г.

Узнать, как обновление Visual Studio 2017 г расширяемости проектов и манифесты VSIX, см. [как: перенос проектов расширяемости для Visual Studio 2017 г](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Пользовательские шаблоны проектов и элементов

Начиная с Visual Studio 2017 г., проверка на наличие пользовательский проект и шаблоны элементов больше не выполняется. Вместо этого расширения необходимо указать файлы манифеста шаблона, описывающие эти шаблоны расположения установки. Можно использовать Visual Studio 2017 г. Чтобы обновить расширения VSIX. При развертывании расширения с помощью MSI, необходимо создать файлы манифеста шаблона вручную. Дополнительные сведения см. в разделе [обновление пользовательских шаблонов проектов и элементов для Visual Studio 2017 г](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Схема манифеста шаблона документирован в [Visual Studio манифеста Справочник по схеме шаблонов](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Рекомендации по производительности обновленного расширения

Новая [как: диагностики производительности расширение](how-to-diagnose-extension-performance.md) подраздела [управления пакеты VSPackage](managing-vspackages.md) показано, как обнаруживать и анализировать воздействие расширения в Visual Studio при запуске и решение загрузить раз.
