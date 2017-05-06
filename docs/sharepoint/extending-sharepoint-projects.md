---
title: "Extending SharePoint Projects"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Projects
  Расширение проекта следует создавать, если для проектов SharePoint нужно настроить функции уровня проекта.  Например, можно добавить пользовательские свойства проекта или обработать события уровня проекта, создаваемые при разработке решения SharePoint в Visual Studio.  
  
## Создание расширений проектов  
 Чтобы расширить элемент проекта, необходимо построить сборку расширения Visual Studio, которая реализует интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Дополнительные сведения см. в разделе [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 При создании расширения проекта есть возможность добавить следующие функции к проектам SharePoint.  
  
-   Добавление элемента контекстного меню.  Пункт меню отображается при открытии контекстное меню для узла проекта SharePoint в **Обозреватель решений**, щелкнув правой кнопкой мыши узел или выберите его и затем выбрать ключи миграцию \+ F10.  Дополнительные сведения см. в разделе [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Добавление пользовательского свойства.  Свойство отображается в окне **Свойства** при выборе проекта SharePoint в **Обозреватель решений**.  Дополнительные сведения см. в разделе [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Пошаговое руководство по созданию, развертыванию и тестированию расширения проекта см. в разделе [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## Общие сведения о связи между расширениями проекта и экземплярами проекта  
 При создании расширения проекта это расширение загружается, когда любой проект SharePoint открывается в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] содержит несколько шаблонов проектов SharePoint, таких как список определений, типы контента и приемники события.  Однако существует всего один тип проекта SharePoint.  Типы проектов, отображаемые в диалоговом окне **Новый проект**, — это только шаблоны, в которых объединены один или несколько элементов проекта SharePoint.  Поскольку тип проекта SharePoint только один, расширения, созданные для одного проекта, применимы ко всем проектам SharePoint.  Например, нельзя создать расширение, применимое только к проекту **Типа контента**.  
  
 Для доступа к определенным экземплярам проекта выполните обработку одного из событий <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> параметра *projectService* реализации метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>.  Например, чтобы определить время добавления проекта SharePoint к решению, выполните обработку события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>.  Дополнительные сведения см. в разделе [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## См. также  
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  