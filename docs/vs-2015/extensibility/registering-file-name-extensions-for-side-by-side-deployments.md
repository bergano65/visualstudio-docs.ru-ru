---
title: Регистрация расширений имен файлов для развертываний Side-By-Side | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e80aa90c5fcb6d223e63df6ed740e0295dd3adf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572736"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений имен файлов для параллельных развертываний
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Регистрация расширений имен файлов для развертываний Side-By-Side](https://docs.microsoft.com/visualstudio/extensibility/registering-file-name-extensions-for-side-by-side-deployments).  
  
Для пакетов VSPackage, развернутых в среде side-by-side, необходимо зарегистрировать расширения имен файлов, чтобы связать файлы с правильной версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Если вы не используете расширение имени файла с конкретной версией, регистрация позволяет пользователям откройте проект и элемент файлы проекта в соответствующую версию [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Сведения о расширениях имен файлов](../extensibility/about-file-name-extensions.md)  
 Описывает, как зарегистрированных расширений имен файлов.  
  
 [Указание обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Сведения о том, как зарегистрировать приложения, которые можно открыть, изменить и т.д., определенный расширением.  
  
 [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md)  
 В этой статье описывается регистрация команд.  
  
 [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md)  
 Описывает, как обрабатывать side-by-side установок, в котором на конкретную версию [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] должны вызываться для открытия файла.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Описывает проблемы, связанные с несколькими версиями [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и VSPackage во время разработки и развертывания для конечных пользователей.

