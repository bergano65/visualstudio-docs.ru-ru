---
title: "How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type | Microsoft Docs"
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
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type
  При определении пользовательского типа элемента проекта SharePoint ему можно добавить пункт контекстного меню.  Этот пункт меню отображается, когда пользователь щелкает правой кнопкой мыши элемент проекта в **Обозревателе решений**.  
  
 В описании следующих действий предполагается, что читатель уже определил собственный тип элемента проекта SharePoint.  Дополнительные сведения см. в разделе [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### Добавление пункта контекстного меню в пользовательский тип элемента проекта  
  
1.  В методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> выполните обработку события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> параметра *projectItemTypeDefinition*.  
  
2.  В обработчике событий для события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> добавьте новый объект <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> в коллекцию <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> или <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> параметра аргументов события.  
  
3.  В обработчике событий <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> для нового объекта <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> выполните задачи необходимо выполнить, когда пользователь выбирает элемент контекстного меню.  
  
## Пример  
 В следующем примере кода демонстрируется добавление пункта контекстного меню к пользовательскому типу элемента проекта.  При открытии пользователем контекстное меню элемента проекта в **Обозреватель решений** и выберите пункт меню **Записывает сообщение в окно вывод** Visual Studio отображает сообщение в окне **Вывод**.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypemenu.vb#4)]  
  
 В этом примере используется служба проекта SharePoint для записи сообщения в окно **Выходные данные**.  Дополнительные сведения см. в разделе [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Компиляция кода  
 Для этого примера требуется проект библиотеки классов со ссылками на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание элемента проекта  
 Чтобы другие разработчики также могли использовать созданный элемент проекта, создайте шаблон проекта или шаблон элемента проекта.  Дополнительные сведения см. в разделе [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Чтобы развернуть элемент проекта, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки, шаблона и всех остальных файлов, которые предполагается распространять с элементом проекта.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  