---
title: Регистрация расширений имен файлов для параллельного IDE
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
ms.openlocfilehash: 68c343646055e6ce877d7bd15892ab1db0d0cbc5
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741709"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений имен файлов для параллельных развертываний
Для пакетов VSPackage, развернутых в параллельной среде, необходимо зарегистрировать расширения имен файлов, чтобы связать их с правильной версией [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Если вы не используете расширение имени файла для конкретной версии, регистрация позволяет пользователям открыть проект и файлы элементов проекта в соответствующей версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Содержание раздела
- [О расширениях имен файлов](../extensibility/about-file-name-extensions.md) Описание регистрации расширений имен файлов.

- [Определение обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Содержит сведения о регистрации приложений, которые могут открывать, изменять и т. д., определенного расширения имени файла.

- [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md) Описывает, как зарегистрировать глаголы.

- [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md) Описывает, как обрабатывать параллельные установки, в которых необходимо вызвать определенную версию, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] чтобы открыть файл.

## <a name="related-sections"></a>Связанные разделы
- [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Описывает проблемы, связанные с несколькими версиями пакета [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage во время разработки и развертывания для конечных пользователей.
