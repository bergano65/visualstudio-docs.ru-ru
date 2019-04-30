---
title: Регистрация расширений имен файлов для развертываний Side-By-Side | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 996f911f37b8226065feb4da311f736dd910550b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805991"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений имен файлов для развертываний side-by-side
Для пакетов VSPackage, развернутых в среде side-by-side, необходимо зарегистрировать расширения имен файлов, чтобы связать файлы с правильной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Если вы не используете расширение имени файла с конкретной версией, регистрация позволяет пользователям откройте проект и элемент файлы проекта в соответствующую версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Содержание раздела
- [О расширения имен файлов](../extensibility/about-file-name-extensions.md) рассматриваются как зарегистрированных расширений имен файлов.

- [Укажите обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md) предоставляет сведения о том, как зарегистрировать приложения, которые можно открыть, изменить и т.д., определенный расширением.

- [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md) описывается регистрация команд.

- [Управление сопоставлениями файлов side-by-side](../extensibility/managing-side-by-side-file-associations.md) обсуждается способ обработки side-by-side установок, в котором на конкретную версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] должны вызываться для открытия файла.

## <a name="related-sections"></a>Связанные разделы
- [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) описаны проблемы, связанные с несколькими версиями [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и VSPackage во время разработки и развертывания для конечных пользователей.