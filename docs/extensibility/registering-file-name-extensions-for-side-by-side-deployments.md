---
title: Регистрация расширений имен файлов для параллельного IDE
description: Сведения о регистрации расширений имен файлов для параллельных развертываний, которые позволяют пользователям открывать файлы в соответствующей версии Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66413890f0aaa08e09a291f5bf31a44e7c24706
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863031"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений имен файлов для параллельных развертываний
Для пакетов VSPackage, развернутых в параллельной среде, необходимо зарегистрировать расширения имен файлов, чтобы связать их с правильной версией [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Если вы не используете расширение имени файла для конкретной версии, регистрация позволяет пользователям открыть проект и файлы элементов проекта в соответствующей версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>В этом разделе
- [О расширениях имен файлов](../extensibility/about-file-name-extensions.md) Описание регистрации расширений имен файлов.

- [Определение обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Содержит сведения о регистрации приложений, которые могут открывать, изменять и т. д., определенного расширения имени файла.

- [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md) Описывает, как зарегистрировать глаголы.

- [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md) Описывает, как обрабатывать параллельные установки, в которых необходимо вызвать определенную версию, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] чтобы открыть файл.

## <a name="related-sections"></a>Связанные разделы
- [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Описывает проблемы, связанные с несколькими версиями пакета [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage во время разработки и развертывания для конечных пользователей.
