---
title: Регистрация расширений имен файлов для боковых развертываний (ru) Документы Майкрософт
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
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701539"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений имени файла для бок о бок развертывания
Для VSPackages, развернутых в среде, размещенной в боковой среде, необходимо зарегистрировать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]расширения имен файлов, чтобы связать файлы с правильной версией. Если вы не используете расширение имени файла для конкретной версии, регистрация [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]позволяет пользователям открывать файлы проекта и элемента проекта в соответствующей версии.

## <a name="in-this-section"></a>В этом разделе
- [О расширении имен файлов](../extensibility/about-file-name-extensions.md) Обсуждает, как регистрируются расширения имен файлов.

- [Указать обработчики файлов для расширения имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Предоставляет информацию о том, как зарегистрировать приложения, которые могут открываться, отсваиваться и так далее, конкретное расширение имени файла.

- [Регистрация глаголов для расширения имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md) Обсуждает, как зарегистрировать глаголы.

- [Управление бок о бок ассоциации файлов](../extensibility/managing-side-by-side-file-associations.md) Обсуждает, как обрабатывать бок о бок установки, в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] которых определенная версия должна быть вызвана, чтобы открыть файл.

## <a name="related-sections"></a>См. также
- [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Описывает проблемы, связанные с несколькими [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] версиями и ВАШИМ VSPackage во время разработки и развертывания для конечных пользователей.
