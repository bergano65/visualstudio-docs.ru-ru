---
title: "Как: доступ к службе SharePoint Project | Документы Microsoft"
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
helpviewer_keywords: SharePoint project service
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 44fd32f579eb6d8f27d9eddf00be946349c4bc86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Практическое руководство. Извлечение службы проектов SharePoint
  Вы можете использовать службы проектов SharePoint в следующих типов решений:  
  
-   Расширение системы проектов SharePoint, например проект расширения, расширения элемента проекта или определении типа элемента проекта. Дополнительные сведения об этих типах расширений см. в разделе [расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Расширение **подключения SharePoint** узел в **обозревателя серверов**. Дополнительные сведения об этих типах расширений см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Другой тип расширения Visual Studio, такие как VSPackage.  
  
## <a name="retrieving-the-service-in-project-system-extensions"></a>Обращение к службе в расширениях системы проектов  
 В каких-либо расширений системы проектов SharePoint можно обращаться к службе проекта с помощью <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объекта.  
  
 Служба проекта также можно получить с помощью следующих процедур.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Обращение к службе в расширении проекта  
  
1.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейсом, найдите <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метод.  
  
2.  Используйте *projectService* параметр для доступа к службе.  
  
     В следующем примере кода демонстрируется использование службы проектов для записи сообщения для **вывода** окна и **список ошибок** окне в расширении простого проекта.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Дополнительные сведения о создании расширений проекта см. в разделе [как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Обращение к службе в расширение элемента проекта  
  
1.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> интерфейсом, найдите <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метод.  
  
2.  Используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> свойство *изменить* параметр обращение к службе.  
  
     В следующем примере кода демонстрируется использование службы проектов для записи сообщения для **вывода** окна и **список ошибок** окна в простое расширение **определение списка** элемент проекта.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Дополнительные сведения о создании расширений элемента проекта см. в разделе [как: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Обращение к службе в определении типа элемента проекта  
  
1.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейсом, найдите <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод.  
  
2.  Используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> свойство *typeDefinition* параметр обращение к службе.  
  
     В следующем примере кода демонстрируется использование службы проектов для записи сообщения для **вывода** окна и **список ошибок** окна в определении типа элемента простого проекта.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Дополнительные сведения об определении типов элемента проекта см. в разделе [как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieving-the-service-in-server-explorer-extensions"></a>Обращение к службе в расширениях обозревателя сервера  
 В расширении **подключения SharePoint** узел в **обозревателя серверов**, доступ к службе проекта с помощью <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> объекта.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Обращение к службе в расширении обозревателя серверов  
  
1.  Получить <xref:System.IServiceProvider> объекта из <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> объекта расширения.  
  
2.  Используйте <xref:System.IServiceProvider.GetService%2A> метод для запроса <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта.  
  
     В следующем примере кода демонстрируется использование службы проектов для записи сообщения для **вывода** окна и **список ошибок** окна с помощью контекстного меню, добавляемого расширением для перечисления узлов в **Обозреватель серверов**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Дополнительные сведения о расширении **подключения SharePoint** узел в **обозревателя серверов**, в разделе [как: расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieving-the-service-in-other-visual-studio-extensions"></a>Обращение к службе в других расширений Visual Studio  
 Можно извлечь проект службы в VSPackage или из любого расширения Visual Studio, которая имеет доступ к <xref:EnvDTE80.DTE2> объекта в объектной модели автоматизации, например в мастере шаблонов проектов, который реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейса.  
  
 В пакете VSPackage, вы можете запросить <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта с помощью одного из следующих методов:  
  
-   <xref:System.IServiceProvider.GetService%2A> Метод управляемого пакета VSPackage, который является производным от <xref:Microsoft.VisualStudio.Shell.Package> класса. Дополнительные сведения см. в разделе [как: доступ к службе](../extensibility/how-to-get-a-service.md).  
  
-   Статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод. Дополнительные сведения см. в разделе [использование GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
 В расширение Visual Studio, которая имеет доступ к <xref:EnvDTE80.DTE2> объекта, можно запросить <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объектов с помощью <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> метод <xref:Microsoft.VisualStudio.Shell.ServiceProvider> объекта. Дополнительные сведения см. в разделе [Получение службы из объекта DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>См. также  
 [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Как: доступ к службе](../extensibility/how-to-get-a-service.md)   
 [Практическое руководство. Использование мастеров для шаблонов проекта](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  