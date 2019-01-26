---
title: Расширение системы проектов SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9f461cae21dfd43bb8fb1d78af65e0ea234d0100
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869269"
---
# <a name="extend-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint
  С помощью набора шаблонов проектов и шаблонов элементов в Visual Studio можно создавать решения SharePoint. Эти шаблоны, требованиям многих сценариев разработки, однако вы можете столкнуться некоторых случаях, где они не предоставляют функциональные возможности, которые нужны. В этих случаях можно расширить системы проектов SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Обзор системы проектов SharePoint
 Системы проектов SharePoint основан на фундаментальной составной частью *элементы проекта SharePoint*. Элемент проекта SharePoint представляет одну настройку SharePoint, например определение списка, веб-части или тип содержимого.  
  
 Проект SharePoint — это проект Visual Studio, которая включает один или несколько элементов проекта SharePoint. Проекты SharePoint также содержат дополнительные компоненты, которые определяют способ группировки элементов проекта в компоненты и пакеты для развертывания.  
  
 Дополнительные сведения о содержимом элементов проекта SharePoint и проектов SharePoint, см. в разделе [создание элементов, шаблоны и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint
 Системы проектов SharePoint можно расширить одним из следующих способов:  
  
-   Определение собственных типов элементов проектов SharePoint и связать их с шаблонами новых элементов или шаблонов проектов в Visual Studio. Например можно определить тип элемента проекта SharePoint для создания настраиваемого действия или поля. Дополнительные сведения см. в разделе [определения пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Расширение типов элементов проектов SharePoint, которые уже установлены в Visual Studio. Например, можно добавить пункта контекстного меню в элемент проекта в **обозревателе решений** и настройки элемента проекта, когда разработчик выбирает элемент меню. Дополнительные сведения см. в разделе [элементы проекта SharePoint, расширить](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Расширение проектов SharePoint. Например можно добавить обработчики событий могут выполнять определенные задачи, когда элементы добавляются или удаляются из проектов SharePoint. Дополнительные сведения см. в разделе [проектов расширения SharePoint](../sharepoint/extending-sharepoint-projects.md).  
  
-   Расширьте поведение упаковки и развертывания проектов SharePoint и элементы проектов SharePoint. Например можно создать собственные шаги развертывания для выполнения при развертывании или отзыве проекта, или можно выполнять дополнительные пользовательские задачи, когда Visual Studio выполняет определенные шаги по развертыванию. Дополнительные сведения см. в разделе [SharePoint расширение упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Часто встречающихся задач разработки
 Нужно выполнить следующие общие задачи в расширениях системы проектов SharePoint.  
  
-   Сохраните пользовательскую строку данных с элементами проекта и в различных типах файлов проекта. Дополнительные сведения см. в разделе [сохранения данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Преобразование объекта в системе проектов SharePoint в соответствующий объект в объектной модели автоматизации Visual Studio или объектной модели интеграции и наоборот. Дополнительные сведения см. в разделе [преобразовать между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>См. также
 [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Расширения инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Концепции и функции программирования для расширений SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
