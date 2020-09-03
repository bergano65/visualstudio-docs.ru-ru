---
title: Регистрация расширений имен файлов для параллельных развертываний | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163697"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений имен файлов для параллельных развертываний
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для пакетов VSPackage, развернутых в параллельной среде, необходимо зарегистрировать расширения имен файлов, чтобы связать их с правильной версией [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Если вы не используете расширение имени файла для конкретной версии, регистрация позволяет пользователям открыть проект и файлы элементов проекта в соответствующей версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>в этом разделе  
 [Сведения о расширениях имен файлов](../extensibility/about-file-name-extensions.md)  
 Описание регистрации расширений имен файлов.  
  
 [Указание обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Содержит сведения о регистрации приложений, которые могут открывать, изменять и т. д., определенного расширения имени файла.  
  
 [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Описывает, как зарегистрировать глаголы.  
  
 [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md)  
 Описывает, как обрабатывать параллельные установки, в которых необходимо вызвать определенную версию, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] чтобы открыть файл.  
  
## <a name="related-sections"></a>См. также  
 [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Описываются проблемы, связанные с несколькими версиями [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и VSPackage во время разработки и развертывания для конечных пользователей.
