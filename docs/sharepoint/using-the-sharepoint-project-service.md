---
title: "Using the SharePoint Project Service | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: bfb6cbc7-6c28-4e1a-abb4-88f149e7712c
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Using the SharePoint Project Service
  Система проектов SharePoint включает службу Project, которую можно использовать для выполнения задач, относящихся к системе проектов.  Служба Project — это объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  
  
 Доступ к службе Project SharePoint можно получить из любого расширения инструментов SharePoint.  Доступ к ней также можно получить из других типов расширений Visual Studio, например из надстроек и пакетов VSPackages.  Дополнительные сведения см. в разделе [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)  
  
## Функции службы Project  
 В следующей таблице перечислены задачи, которые можно выполнять с помощью службы Project SharePoint и используемый метод или свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> для выполнения каждой из задач.  
  
|Задача|Используемый член|  
|------------|-----------------------|  
|Доступ к любому проекту SharePoint, открытому в Visual Studio.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|  
|Доступ ко всем доступным типам элементов проектов SharePoint \(включая встроенные и пользовательские типы элементов проекта\).|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|  
|Доступ ко всем шагам развертывания, которые доступны для проектов SharePoint \(включая встроенные и пользовательские шаги развертывания\).|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|  
|Доступ к событиям, возникающим, когда разработчик выполняет рефакторинг кода в проекте SharePoint.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|  
|Выполнение пользовательской *команды SharePoint*, обращающейся к объектной модели сервера SharePoint.  Дополнительные сведения о командах SharePoint см. в разделе [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|  
|Преобразование типа из системы проектов SharePoint в тип из объектной модели автоматизации Visual Studio или объектной модели интеграции и наоборот.  Дополнительные сведения см. в разделе [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)|Метод <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|  
|Запись сообщений в окно **вывода** или в окно **списка ошибок** в Visual Studio.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|  
|Доступ к другим службам, доступным в Visual Studio.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|  
|Получение пути к папке установки локального сайта SharePoint, который используется для отладки решения.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|  
|Определение того, что именно установлено на компьютере: [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] или [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)].|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|  
|Проверка компонента или пакета решения SharePoint.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|  
  
## См. также  
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Практическое руководство. Обращение к службе из объекта DTE](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  