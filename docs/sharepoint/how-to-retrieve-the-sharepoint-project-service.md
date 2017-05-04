---
title: "How to: Retrieve the SharePoint Project Service | Microsoft Docs"
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
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: Retrieve the SharePoint Project Service
  К службе проектов SharePoint можно обращаться в решениях следующих типов.  
  
-   Расширении системы проектов SharePoint, например расширении проекта, расширении элемента проекта или определении типа элемента проекта.  Дополнительные сведения об этих типах расширений см. в разделе [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Расширениях узла **Подключения SharePoint** в **обозревателе сервера**.  Дополнительные сведения об этих типах расширений см. в разделе [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Расширении Visual Studio иного типа, например надстройке или VSPackage.  
  
## Обращение к службе в расширениях системы проектов  
 Во всех расширениях системы проектов SharePoint к службе проектов можно обращаться с помощью свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  
  
 К службе проектов можно также обращаться с помощью следующих процедур.  
  
#### Обращение к службе в расширении проекта  
  
1.  В реализации интерфейса <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> найдите метод <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>.  
  
2.  Для обращения к службе воспользуйтесь параметром *projectService*.  
  
     В следующем примере кода показано, как с помощью службы проекта написать сообщение в окне **Выходные данные** и окне **Список ошибок** в простом расширении проекта.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#1)]  
  
     Дополнительные сведения о создании расширений проекта см. в разделе [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### Обращение к службе в расширении элемента проекта  
  
1.  В реализации интерфейса <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> найдите метод <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>.  
  
2.  Для обращения к службе воспользуйтесь свойством <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> параметра *projectItemType*.  
  
     В следующем примере кода показано, как с помощью службы проекта написать сообщение в окне **Выходные данные** и окне **Список ошибок** в простом расширении элемента проекта **Определение списка**.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#2)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#2)]  
  
     Дополнительные сведения о создании расширений элемента проекта см. в разделе [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### Обращение к службе в определении типа элемента проекта  
  
1.  В реализации интерфейса <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> найдите метод <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  
  
2.  Для обращения к службе воспользуйтесь свойством <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> параметра *typeDefinition*.  
  
     В следующем примере кода показано, как с помощью службы проекта написать сообщение в окне **Выходные данные** и окне **Список ошибок** в простом определении типа элемента проекта.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#3)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#3)]  
  
     Дополнительные сведения об определении типов элемента проекта см. в разделе [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Обращение к службе в расширениях обозревателя сервера  
 В расширении узла **Подключения SharePoint** в **обозревателе сервера** к службе проекта можно обращаться с помощью свойства <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>.  
  
#### Обращение к службе в расширении обозревателя сервера  
  
1.  Получите объект <xref:System.IServiceProvider> из свойства <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> в своем расширении.  
  
2.  Воспользуйтесь методом <xref:System.IServiceProvider.GetService%2A> для запроса объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  
  
     В следующем примере кода показано, как с помощью службы проекта написать сообщение в окне **Выходные данные** и окне **Список ошибок** с помощью контекстного меню, добавляемого расширением для перечисления узлов в **обозревателе сервера**.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/vb/extension/extension.vb#1)]  
  
     Дополнительные сведения о расширении узла **Подключения SharePoint** в **обозревателе сервера** см. в разделе [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Обращение к службе в других расширениях Visual Studio  
 К службе проекта можно обращаться в VSPackage или любом другом расширении Visual Studio с доступом к объекту <xref:EnvDTE80.DTE2> в объектной модели автоматизации, например в надстройке или мастере шаблонов проектов, реализующем интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
 В VSPackage объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> можно запросить с помощью одного из следующих методов.  
  
-   Метода <xref:System.IServiceProvider.GetService%2A> управляемого пакетом VSPackage, производным от класса <xref:Microsoft.VisualStudio.Shell.Package>.  Дополнительные сведения см. в разделе [Практическое руководство: Получение службы](~/extensibility/how-to-get-a-service.md).  
  
-   Статического метода <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>.  Дополнительные сведения см. в разделе [Практическое руководство. Использование GetGlobalService](~/misc/how-to-use-getglobalservice.md).  
  
 В расширении Visual Studio с доступом к объекту <xref:EnvDTE80.DTE2> можно запросить объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> с помощью метода <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> объекта <xref:Microsoft.VisualStudio.Shell.ServiceProvider>.  Дополнительные сведения см. в разделе [Практическое руководство. Получение службы из объекта DTE](~/misc/how-to-get-a-service-from-the-dte-object.md).  
  
### Пример  
 В следующем примере кода показано, как обратиться к службе проекта в надстройке Visual Studio.  Чтобы воспользоваться этим кодом, выполните его из класса `Connect` в проекте надстройки.  Объект `_applicationObject` создается в проектах надстройки автоматически; этот объект является экземпляром интерфейса <xref:EnvDTE80.DTE2>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#1)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#1)]  
  
 Для этого примера необходимо следующее.  
  
-   Проект надстройки Visual Studio.  Дополнительные сведения см. в разделе [Практическое руководство. Создание надстройки](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce).  
  
-   Ссылки на сборки Microsoft.VisualStudio.OLE.Interop, Microsoft.VisualStudio.Shell и Microsoft.VisualStudio.SharePoint.  
  
## См. также  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Практическое руководство. Создание надстройки](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)   
 [Практическое руководство: Получение службы](~/extensibility/how-to-get-a-service.md)   
 [Практическое руководство. Получение службы из объекта DTE](~/misc/how-to-get-a-service-from-the-dte-object.md)   
 [Практическое руководство. Использование мастеров для шаблонов проекта](~/extensibility/how-to-use-wizards-with-project-templates.md)  
  
  