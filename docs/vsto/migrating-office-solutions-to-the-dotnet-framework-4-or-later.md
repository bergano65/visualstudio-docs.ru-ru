---
title: "Перенос решений Office на платформу .NET Framework 4 или более поздней версии | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.TargetFrameworkWarning"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "проекты Office [разработка решений Office в Visual Studio], миграция на .NET Framework 4"
ms.assetid: 31f6c48b-c086-4362-8629-f644d6083a44
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Перенос решений Office на платформу .NET Framework 4 или более поздней версии
  Если требуемая версия .NET Framework проекта Office изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию с более ранней, по\-прежнему могут потребоваться некоторые дополнительные действия для запуска решения на компьютерах разработчика и пользователя. Для получения дополнительной информации см. [Изменения, необходимые для выполнения проектов Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Кроме того, проект может перестать компилироваться. Некоторые функции проектов Office используют разные модели программирования для различных версий платформы .NET Framework. При изменении целевой платформы проекта Office на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию необходимо внести следующие изменения в код проекта:  
  
-   [Обновление проектов Excel и Word, которые переносятся в .NET Framework 4 или .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Обновление настроек ленты в проектах Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Обновление областей формы в проектах Outlook, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Требуемая версия .NET Framework проекта Office изменяется при его обновлении с более ранней версии Visual Studio. Для получения дополнительной информации см. [Обновление и перенос решений Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Дополнительные сведения о том, почему некоторые компоненты проектов Office имеют другую модель программирования, если предназначаются для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, см. в разделах [Изменения проектирования проектов Office, предназначенных для .NET Framework 4 или .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) и [Общие сведения об инструментах Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## См. также  
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Практическое руководство. Определение целевой версии .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Устранение ошибок в решениях Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Дополнительные сведения об ошибках в решениях Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  