---
title: Перенос решений Office для .NET Framework 4 или более поздней версии | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 830dcdb9e42472aa712c86ddb117b3b8003ac4d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Перенос решений Office на платформу .NET Framework 4 или более поздней версии
  Если требуемая версия .NET Framework проекта Office изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию с более ранней, по-прежнему могут потребоваться некоторые дополнительные действия для запуска решения на компьютерах разработчика и пользователя. Дополнительные сведения см. в разделе [необходимые изменения для выполнения проектов Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Кроме того, проект может перестать компилироваться. Некоторые функции проектов Office используют разные модели программирования для различных версий платформы .NET Framework. При изменении целевой платформы проекта Office на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию необходимо внести следующие изменения в код проекта:  
  
-   [Обновление проектов Excel и Word, переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Обновление настроек ленты в проектах Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Обновление областей формы в проектах Outlook, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Требуемая версия .NET Framework проекта Office изменяется при его обновлении с более ранней версии Visual Studio. Для получения дополнительной информации см. [Upgrading and Migrating Office Solutions](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Дополнительные сведения о том, почему некоторые компоненты проектов Office имеют другую модель программирования при разработке [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, см. раздел [изменения разработки проектов Office, предназначенных для .NET Framework 4 или .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) и [средств Visual Studio для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>См. также  
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [How to: Target a Version of the .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)  (Практическое руководство. Нацеливание на определенную версию .NET Framework)  
 [Устранение неполадок в решениях Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Дополнительные сведения об ошибках в решениях Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  