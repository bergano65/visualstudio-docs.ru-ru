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
ms.openlocfilehash: 7a21c4f330d78d35735cb8463af62802d1fa21a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961667"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений имен файлов для развертываний side-by-side
Для пакетов VSPackage, развернутых в среде side-by-side, необходимо зарегистрировать расширения имен файлов, чтобы связать файлы с правильной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Если вы не используете расширение имени файла с конкретной версией, регистрация позволяет пользователям откройте проект и элемент файлы проекта в соответствующую версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Содержание раздела  
 [О расширения имен файлов](../extensibility/about-file-name-extensions.md)  
 Описывает, как зарегистрированных расширений имен файлов.  
  
 [Укажите обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Сведения о том, как зарегистрировать приложения, которые можно открыть, изменить и т.д., определенный расширением.  
  
 [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md)  
 В этой статье описывается регистрация команд.  
  
 [Управление сопоставлениями файлов side-by-side](../extensibility/managing-side-by-side-file-associations.md)  
 Описывает, как обрабатывать side-by-side установок, в котором на конкретную версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] должны вызываться для открытия файла.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Описываются проблемы, связанные с несколькими версиями [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и VSPackage во время разработки и развертывания для конечных пользователей.