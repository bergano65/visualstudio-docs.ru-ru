---
title: "Converting Between SharePoint Project System Types and Other Visual Studio Project Types | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Converting Between SharePoint Project System Types and Other Visual Studio Project Types
  В некоторых случаях разработчику, у которого имеется объект в системе проектов SharePoint, могут потребоваться функции соответствующего объекта в объектной модели автоматизации или интеграции Visual Studio, либо наоборот.  В этом случае для преобразования объекта в объект другой объектной модели можно воспользоваться методом <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> службы проекта SharePoint.  
  
 Например, у разработчика может быть объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>, но ему могут требоваться методы, которые доступны только в объекте <xref:EnvDTE.Project> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  В этом случае можно с помощью метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> преобразовать объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> в <xref:EnvDTE.Project> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Сведения об объектной модели автоматизации и интеграции Visual Studio см. в разделе [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Типы преобразования  
 В следующей таблице перечислены типы, которые можно преобразовывать с помощью этого метода из системы проектов SharePoint в другую объектную модель Visual Studio и наоборот.  
  
|Тип системы проектов SharePoint|Соответствующие типы в объектных моделях автоматизации и интеграции|  
|-------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> или<br /><br /> Любой интерфейс в объектной модели интеграции Visual Studio, реализуемый базовым COM\-объектом проекта.  К таким интерфейсам относятся <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> \(и производные от него интерфейсы\) и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  Список главных интерфейсов, реализуемых в проектах, см. в разделе [Основные компоненты модели проекта](../extensibility/internals/project-model-core-components.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> или<br /><br /> Значение типа <xref:System.UInt32> \(также называемое VSITEMID\), которое определяет элемент проекта в содержащем его объекте <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.  Это значение может быть передано параметру *itemid* или каким\-либо методам <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.|  
  
## Пример  
 В следующем примере кода показано, как с помощью метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> преобразовать объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> в объект <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#2)]  
  
 Для этого примера необходимо следующее.  
  
-   Расширение системы проектов SharePoint, которое содержит ссылку на сборку EnvDTE.dll.  Дополнительные сведения см. в разделе [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Код, регистрирующий метод `projectService_ProjectAdded`, для обработки события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  Пример см. в разделе [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## См. также  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  