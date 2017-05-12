---
title: "How to: Add a Shortcut Menu Item to SharePoint Projects"
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
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Add a Shortcut Menu Item to SharePoint Projects
  В элементе проекта SharePoint можно добавить пункт контекстного меню.  Этот пункт меню отображается, когда пользователь щелкает правой кнопкой мыши узел проекта в **Обозревателе решений**.  
  
 В описании следующих действий предполагается, что расширение проекта уже создано.  Дополнительные сведения см. в разделе [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### Добавление пункта контекстного меню в проекты SharePoint  
  
1.  В методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> обработайте событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> параметра *projectService*.  
  
2.  В обработчике событий для события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> добавьте новый объект <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> в коллекцию <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> или <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> параметра аргументов события.  
  
3.  Выполните в обработчике событий <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> для нового объекта <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> задачи, которые должны выполняться при выборе пользователем пункта контекстного меню.  
  
## Пример  
 В следующем примере кода демонстрируется добавление пункта контекстного меню в узел проекта SharePoint в **Обозреватель решений**.  Когда пользователь щелкает правой кнопкой мыши узел проекта и выбирает пункт меню **Написать сообщение в окно выходных данных**, Visual Studio отображает сообщение в окне **Выходные данные**.  В этом примере используется служба проекта SharePoint для отображения сообщения.  Дополнительные сведения см. в разделе [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/vb/extension/projectitemextensionmenu.vb#1)]  
  
## Компиляция кода  
 Для этого примера требуется проект библиотеки классов со ссылками на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание расширения  
 Чтобы развернуть расширение, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  