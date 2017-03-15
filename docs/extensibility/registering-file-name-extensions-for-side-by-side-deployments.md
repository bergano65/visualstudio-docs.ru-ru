---
title: "Регистрация расширений файлов для развертываний Side-By-Side | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 216fb4cc449e8a67178f587b0c199864d267ccf4
ms.lasthandoff: 02/22/2017

---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений файлов для развертываний Side-By-Side
Для развертывания в среде side-by-side VSPackages, необходимо зарегистрировать расширения имен файлов, чтобы сопоставить файлы с правильной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Если не используется расширение имени файла для конкретных версий регистрации позволяет пользователям откройте свой проект и файлы элементов в соответствующую версию проекта [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Содержание  
 [О расширений имен файлов](../extensibility/about-file-name-extensions.md)  
 Описывает, как зарегистрированных расширений имен файлов.  
  
 [Указание обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Сведения о регистрации приложения, которые можно открыть, edit и т.д., расширение имени файла конкретного.  
  
 [Регистрация команды для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Описывает, как зарегистрировать команд.  
  
 [Управление сопоставлениями файлов Side-by-Side](../extensibility/managing-side-by-side-file-associations.md)  
 Описывает, как обрабатывать side-by-side установок, в котором определенной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] должны вызываться для открытия файла.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Описывает проблемы, связанные с несколькими версиями [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и VSPackage во время разработки и развертывания для конечных пользователей.
