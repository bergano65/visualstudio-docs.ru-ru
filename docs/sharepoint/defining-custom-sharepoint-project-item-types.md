---
title: "Defining Custom SharePoint Project Item Types | Microsoft Docs"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Defining Custom SharePoint Project Item Types
  Новый тип элементов проектов SharePoint определяется в тех случаях, когда требуется создать новый вид элементов проектов SharePoint.  Например, Visual Studio не содержит элементов проекта SharePoint для добавления полей или пользовательских действий к сайту SharePoint.  Можно также определить собственные типы элементов проекта SharePoint для создания полей и настраиваемых действий.  
  
## Задачи по определению типов элементов проектов SharePoint  
 Чтобы определить пользовательский тип элемента проекта, необходимо построить сборку расширения Visual Studio, которая реализует интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  Дополнительные сведения см. в разделе [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 При определении пользовательского типа элемента проекта к нему можно добавить следующие функциональные возможности.  
  
-   Добавление пункта контекстного меню в элемент проекта.  Пункт меню отображается при открытии контекстное меню для элемента проекта в **Обозреватель решений**, щелкнув правой кнопкой мыши элемент проекта или путем выбора его и затем выбрать ключи миграцию \+ F10.  Дополнительные сведения см. в разделе [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Добавление пользовательского свойства к элементу проекта.  Свойство отображается в окне **Свойства** при выборе элемента проекта в **Обозреватель решений**.  Дополнительные сведения см. в разделе [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Чтобы другие разработчики также могли использовать созданный элемент проекта в Visual Studio, создайте SPDATA\-файл и шаблон элемента или шаблон проекта, связанный с этим элементом проекта.  Дополнительные сведения см. в разделе [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Общие сведения о связи между типами элементов проектов и экземплярами элементов проектов  
 При определении типа элементов проектов SharePoint Visual Studio загружает расширение в то время, как элементы проектов связанного типа добавляются к проекту SharePoint.  Например, при определении нового типа элементов проектов **настраиваемого действия** Visual Studio загружает расширение в то время, как пользователь добавляет элемент проекта **настраиваемого фильтра** к проекту.  Visual Studio использует один и тот же экземпляр расширения для всех экземпляров связанного типа элементов проектов.  В предыдущем примере при добавлении пользователем второго элемента проекта **настраиваемого действия** к проекту один и тот же экземпляр расширения используется для настройки второго элемента проекта.  
  
 Для доступа к определенным экземплярам типа элементов проектов выполните обработку одного из событий <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> параметра *projectItemTypeDefinition* реализации метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Например, чтобы определить время добавления элемента проекта пользовательского типа к проекту, выполните обработку события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>.  Дополнительные сведения см. в разделе [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## См. также  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  