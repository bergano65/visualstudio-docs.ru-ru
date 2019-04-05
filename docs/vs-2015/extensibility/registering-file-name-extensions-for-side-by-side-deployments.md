---
title: Регистрация расширений имен файлов для развертываний Side-By-Side | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 354b91dd1282df9726c1ee9c47f610b0dfdd9c1a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980881"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений имен файлов для параллельных развертываний
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Описываются проблемы, связанные с несколькими версиями [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и VSPackage во время разработки и развертывания для конечных пользователей.
