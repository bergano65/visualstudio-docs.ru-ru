---
title: "Associating Custom Data with SharePoint Tools Extensions"
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
  - "projects [SharePoint development in Visual Studio], associating custom data"
  - "project items [SharePoint development in Visual Studio], associating custom data"
  - "SharePoint project items, associating custom data"
  - "SharePoint projects, associating custom data"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Associating Custom Data with SharePoint Tools Extensions
  В некоторые объекты в расширениях средств SharePoint можно добавлять пользовательские данные.  Это удобно при наличии в одной из частей расширения данных, к которым нужно будет обращаться позже из другой части кода расширения.  Вместо реализации пользовательского способа хранения данных и доступа к ним можно связать данные с объектом в расширении, а затем извлечь эти данные из этого объекта позже.  
  
 Добавление пользовательских данных в объекты также удобно использовать для сохранения неизменными данных, важных для определенного элемента в Visual Studio.  Расширения средств SharePoint загружаются в Visual Studio только один раз, поэтому расширение может работать с несколькими различными элементами \(например, проектами, элементами проектов или узлами **Server Explorer**\).  При наличии пользовательских данных, имеющих отношение только к определенному элементу, можно добавить эти данные в объект, представляющий этот элемент.  
  
 При добавлении пользовательских данных в объекты в расширениях средств SharePoint эти данные не сохраняются.  Данные доступны только в течение времени существования объекта.  После очистки объекта сборщиком мусора данные будут утрачены.  
  
 В расширениях системы проектов SharePoint также можно сохранить строковые данные, которые должны оставаться неизменными после выгрузки расширения.  Дополнительные сведения см. в разделе [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Объекты, которые могут содержать пользовательские данные  
 Пользовательские данные можно добавить в любой объект объектной модели средств SharePoint, реализующей интерфейс <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>.  Этот интерфейс определяет только одно свойство <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, представляющее собой коллекцию объектов пользовательских данных.  Следующие типы реализуют интерфейс <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## Добавление и извлечение пользовательских данных  
 Чтобы добавить пользовательские данные в объект в расширении средств SharePoint, получите свойство <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> объекта, к которому необходимо добавить данные, а затем воспользуйтесь методом <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> для добавления данных к этому объекту.  
  
 Чтобы извлечь пользовательские данные из объекта в расширении средств SharePoint, получите свойство <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> этого объекта и воспользуйтесь одним из следующих методов.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>.  Этот метод возвращает значение **true**, если объект данных существует; в противном случае — значение **false**.  Этот метод можно использовать для извлечения экземпляров типов значений или ссылочных типов.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>.  Этот метод возвращает объект данных, если он существует, или значение **null** при его отсутствии.  Этот метод можно использовать только для извлечения экземпляров ссылочных типов.  
  
 В следующем примере кода определяется, связан ли определенный объект данных с элементом проекта.  Если объект данных еще не связан с элементом проекта, код добавляет объект в свойство элемента проекта <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>.  Данный пример в контексте полного примера см. в разделе [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#13)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#13)]  
  
## См. также  
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)  
  
  