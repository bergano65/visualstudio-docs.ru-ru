---
title: "Extending the SharePoint Project System | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Project System
  Можно создать решений SharePoint с помощью набора шаблонов и шаблонов элементов проекта в Visual Studio.  Эти шаблоны соответствуют требованиям многих сценариях разработки, но при этом может обнаружить некоторые случаи, когда они не обеспечивают функциональность, которую требуется.  В этих ситуациях можно расширить систему проектов SharePoint.  
  
## Обзор системы проектов SharePoint  
 Система проекта SharePoint основана на фундаментальном компоненте — *элементах проекта SharePoint*.  Элемент проекта SharePoint представляет одну настройку SharePoint, такую как определение списка, веб\-часть или тип содержимого.  
  
 Проект SharePoint — это проект Visual Studio, включающий один или более элементов проекта SharePoint.  Проекты SharePoint также содержат дополнительные компоненты, которые определяют способы группировки элементов проекта в компоненты и пакеты для развертывания.  
  
 Дополнительные сведения о содержимом элементов проектов SharePoint и проектов SharePoint см. в разделе [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Расширение системы проектов SharePoint  
 Систему проектов SharePoint можно расширить одним из следующих способов:  
  
-   Определите пользовательские типы элементов проекта SharePoint и свяжите их с шаблонами новых элементов или с шаблонами проектов в Visual Studio.  Например, можно определить тип элемента проекта SharePoint для создания настраиваемого действия или поля.  Дополнительные сведения см. в разделе [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Выполните расширение типов элементов проектов SharePoint, поставляемых с Visual Studio.  Например, можно добавить элемент контекстного меню с элементом проекта в **Обозреватель решений** и настраивать элемент проекта, когда разработчик выбирает пункт меню.  Дополнительные сведения см. в разделе [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Расширение проектов SharePoint.  Например, можно добавлять обработчики событий для выполнения определенных задач при добавлении элементов в проекты SharePoint или при их удалении из этих проектов.  Дополнительные сведения см. в разделе [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md).  
  
-   Выполните расширение поведения упаковки и развертывания элементов проектов SharePoint или проектов SharePoint.  Например, можно создать собственные шаги по развертыванию, которые будут выполняться при развертывании или при отзыве проекта, либо можно выполнять дополнительные пользовательские задачи, когда среда Visual Studio выполняет определенные шаги по развертыванию.  Дополнительные сведения см. в разделе [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## Типичные задачи разработки  
 С помощью расширений системы проектов SharePoint можно выполнять следующие типичные задачи.  
  
-   Сохранять настраиваемые строковые данные в элементах проектов и в нескольких различных типах файлов проектов.  Дополнительные сведения см. в разделе [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Преобразование объекта в системе проектов SharePoint в соответствующий объект в объектной модели автоматизации или объектной модели интеграции Visual Studio и наоборот.  Дополнительные сведения см. в разделе [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## См. также  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  