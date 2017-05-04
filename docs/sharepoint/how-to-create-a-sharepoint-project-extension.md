---
title: "How to: Create a SharePoint Project Extension | Microsoft Docs"
ms.custom: ""
ms.date: "04/28/2017"
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
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# How to: Create a SharePoint Project Extension
  Расширение проекта создается в случаях, когда требуется добавить функции к открытому в Visual Studio проекту SharePoint.  Дополнительные сведения см. в разделе [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### Создание расширения проекта  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  
  
4.  Добавьте к классу атрибут <xref:System.ComponentModel.Composition.ExportAttribute>.  Этот атрибут позволяет Visual Studio находить и загружать пользовательскую реализацию класса <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Передайте конструктору атрибута тип <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  
  
5.  В текущей реализации метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> с помощью членов параметра *projectService* определите поведение расширения.  Этот параметр представляет собой объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>, который предоставляет доступ к событиям, определенным в интерфейсе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>.  
  
## Пример  
 В следующем примере кода показано создание простого расширения проекта, которое обрабатывает большинство событий проекта SharePoint, определенных интерфейсом <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>.  Чтобы протестировать код, создайте проект SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], а затем добавьте в решение дополнительные проекты, измените значения свойства проекта либо удалите или исключите проект.  Расширение уведомляет о событиях с помощью письменных сообщений в окне **Выходные данные** и окне **Список ошибок**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectextension.cs#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectextension.vb#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/savedatatoprojectfile.vb#3)]  
  
 В этом примере служба проекта SharePoint используется для записи сообщения в окна **Выходные данные** и **Список ошибок**.  Дополнительные сведения см. в разделе [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Примеры кода, демонстрирующие обработку событий <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>, см. в разделах [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) и [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание расширения  
 Чтобы развернуть расширение, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
  
  