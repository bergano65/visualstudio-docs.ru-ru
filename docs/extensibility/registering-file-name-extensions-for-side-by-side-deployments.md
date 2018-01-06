---
title: "Регистрация расширения имен файлов для развертываний Side-By-Side | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 457f9e5303c71d73467815b581c091dc239c1b63
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширения имен файлов для развертываний Side-By-Side
Для развертывания в среде side-by-side пакеты VSPackage, необходимо зарегистрировать расширения имен файлов, чтобы сопоставить файлы с правильной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Если вы не используете расширение имени файла от версии, регистрация позволяет пользователям откройте свой проект и файлы элементов в соответствующую версию проекта [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Сведения о расширениях имен файлов](../extensibility/about-file-name-extensions.md)  
 Описывает, как зарегистрированных расширений имен файлов.  
  
 [Указание обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Сведения о регистрации приложения, которые можно открыть, изменить и т.д., расширение имени файла, определенного.  
  
 [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Описывает, как зарегистрировать команд.  
  
 [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md)  
 Описывает, как обрабатывать side-by-side установок, в котором на конкретную версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] нужно вызывать для открытия файла.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Описывает проблемы, связанные с несколькими версиями [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и VSPackage во время разработки и развертывания для конечных пользователей.