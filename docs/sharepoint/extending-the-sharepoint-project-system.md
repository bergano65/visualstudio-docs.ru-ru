---
title: "Расширение системы проектов SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e79808ef9d5d4712d67426b202046615c8ab14b2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="extending-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint
  Решения SharePoint можно создать с помощью набор шаблонов проектов и элементов в Visual Studio. Эти шаблоны удовлетворяют требованиям многих сценариев разработки, но может обнаружить некоторые случаи, где они не обеспечивают функциональные возможности, которые нужны. В этих случаях можно расширить системы проектов SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Обзор системы проектов SharePoint  
 Системы проектов SharePoint зависит главным компонентом *элементы проектов SharePoint*. Элемент проекта SharePoint представляет одну настройку SharePoint, например определение списка, веб-часть или тип содержимого.  
  
 Проект SharePoint — проект Visual Studio, который содержит один или несколько элементов проекта SharePoint. Проекты SharePoint также содержат дополнительные компоненты, которые определяют способ группировки элементов проекта в компоненты и пакеты для развертывания.  
  
 Дополнительные сведения о содержимом проектов SharePoint и элементов проектов SharePoint см. в разделе [Создание шаблонов элементов и проектов для элементов проекта SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint  
 Системы проектов SharePoint можно расширить одним из следующих способов:  
  
-   Определение собственных типов элементов проектов SharePoint и свяжите их с шаблонами новых элементов или шаблонов проектов в Visual Studio. Например можно определить тип элемента проекта SharePoint для создания настраиваемого действия или поля. Дополнительные сведения см. в разделе [определение типов элементов проектов настраиваемый SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Расширение типов элементов проектов SharePoint, которые уже установлены в Visual Studio. Например, можно добавить контекстное меню для элемента проекта в **обозревателе решений** и настройки элемента проекта, когда разработчик выбирает элемент меню. Дополнительные сведения см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Расширение проектов SharePoint. Например можно добавить обработчики событий для выполнения определенных задач, когда элементы добавлены или удалены из проектов SharePoint. Дополнительные сведения см. в разделе [расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md).  
  
-   Поведения упаковки и развертывания проектов SharePoint и элементы проектов SharePoint. Например можно создать собственные шаги развертывания для выполнения при развертывании или отзыве проекта или дополнительные пользовательские задачи выполняются в том случае, когда среда Visual Studio выполняет определенные шаги по развертыванию. Дополнительные сведения см. в разделе [расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Общие задачи разработки  
 В расширениях системы проектов SharePoint можно выполнять следующие общие задачи:  
  
-   Сохраните настраиваемые строковые данные в элементах проектов и в различных типах файлов проекта. Дополнительные сведения см. в разделе [сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Преобразование объекта в системе проекта SharePoint для соответствующего объекта в объектной модели автоматизации Visual Studio или объектной модели интеграции и наоборот. Дополнительные сведения см. в разделе [преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>См. также  
 [Определение типов элементов проектов SharePoint, пользовательские](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Концепции и функции программирования для расширений SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  