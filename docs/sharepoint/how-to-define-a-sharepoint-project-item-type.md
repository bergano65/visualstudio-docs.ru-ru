---
title: "How to: Define a SharePoint Project Item Type | Microsoft Docs"
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
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# How to: Define a SharePoint Project Item Type
  Если необходимо создать пользовательский элемент проекта SharePoint, требуется определить тип проектного элемента.  Дополнительные сведения см. в разделе [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### Определение типа элементов проектов  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  
  
4.  Добавьте следующие атрибуты к классу:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Этот атрибут позволяет Visual Studio находить и загружать пользовательскую реализацию <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  Передайте конструктору этого атрибута тип <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>;  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  В определении типа элементов проектов этот атрибут задает идентификатор строки для нового элемента проекта.  Чтобы все элементы проекта имели уникальные имена, рекомендуется использовать формат *название\_компании*.*имя\_компонента*.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>.  Этот атрибут задает значок, отображаемый для данного элемента проекта в **Обозревателе решений**.  Данный атрибут является необязательным; если не задать его для класса, в Visual Studio будет отображаться значок по умолчанию для элемента проекта.  При задании этого атрибута передайте ему полное имя значка или растрового изображения, которые внедрены в сборку.  
  
5.  В текущей реализации метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> с помощью членов параметра *projectItemTypeDefinition* определите поведение типа проектного элемента.  Этот параметр представляет собой объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>, который предоставляет доступ к событиям, определенным в интерфейсах <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>.  Для осуществления доступа к конкретному экземпляру типа проектного элемента необходимо обработать события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>, такие как <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Пример  
 В следующем примере кода показано определение простого типа проектного элемента.  Когда пользователь добавляет в проект элемент проекта этого типа, этот тип проектного элемента записывает сообщение в окна **Выходные данные** и **Список ошибок**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemtype.cs#2)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemtype.vb#2)]  
  
 В этом примере служба проекта SharePoint используется для записи сообщения в окна **Выходные данные** и **Список ошибок**.  Дополнительные сведения см. в разделе [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание элемента проекта  
 Чтобы другие разработчики также могли использовать созданный элемент проекта, создайте шаблон проекта или шаблон элемента проекта.  Дополнительные сведения см. в разделе [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Чтобы развернуть элемент проекта, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки, шаблона и всех остальных файлов, которые предполагается распространять с элементом проекта.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  