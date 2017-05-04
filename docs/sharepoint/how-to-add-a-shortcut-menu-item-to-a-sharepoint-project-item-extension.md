---
title: "How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension
  Чтобы добавить пункт контекстного меню в существующий элемент проекта SharePoint, можно воспользоваться расширением элемента проекта.  Этот пункт меню отображается, когда пользователь щелкает правой кнопкой мыши элемент проекта в **Обозревателе решений**.  
  
 В описании следующих действий предполагается, что расширение элемента проекта уже создано.  Дополнительные сведения см. в разделе [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### Добавление пункта контекстного меню в расширение элемента проекта  
  
1.  В методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> обработайте событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> параметра *projectItemType*.  
  
2.  В обработчике событий для события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> добавьте новый объект <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> в коллекцию <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> или <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> параметра аргументов события.  
  
3.  Выполните в обработчике событий <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> для нового объекта <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> задачи, которые должны выполняться при выборе пользователем пункта контекстного меню.  
  
## Пример  
 В следующем примере кода демонстрируется добавление пункта контекстного меню в элемент проекта приемника событий.  Когда пользователь щелкает правой кнопкой мыши элемент проекта в **Обозревателе решений** и выбирает пункт меню **Написать сообщение в окно выходных данных**, Visual Studio отображает сообщение в окне **Выходные данные**.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionmenu.vb#1)]  
  
 В этом примере используется служба проекта SharePoint для записи сообщения в окно **Выходные данные**.  Дополнительные сведения см. в разделе [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Компиляция кода  
 Для этого примера требуется проект библиотеки классов со ссылками на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание расширения  
 Чтобы развернуть расширение, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  