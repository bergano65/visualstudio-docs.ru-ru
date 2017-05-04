---
title: "How to: Create a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create a SharePoint Project Item Extension
  Расширение элемента создается в случаях, когда требуется добавить функции к уже установленному в Visual Studio элементу проекта SharePoint.  Дополнительные сведения см. в разделе [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
### Создание расширения элемента проекта  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  
  
4.  Добавьте следующие атрибуты к классу:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Этот атрибут позволяет Visual Studio находить и загружать пользовательскую реализацию <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Передайте конструктору этого атрибута тип <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>;  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  В расширении элемента проекта этот атрибут определяет элемент проекта, которые требуется расширить.  Передайте идентификатор проектного элемента конструктору атрибутов.  Список идентификаторов элементов проектов, входящих в состав Visual Studio см. в разделе [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  В текущей реализации метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> с помощью членов параметра *projectItemType* определите поведение расширения.  Этот параметр представляет собой объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>, который предоставляет доступ к событиям, определенным в интерфейсах <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>.  Для осуществления доступа к конкретному экземпляру расширяемого типа проектного элемента необходимо обработать события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>, такие как <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Пример  
 В следующем примере кода показано, как создать простое расширение для элемента проекта приемника событий.  Всякий раз когда пользователь добавляет в проект SharePoint проектный элемент приемника событий, это расширение записывает сообщение в окна **Выходные данные** и **Список ошибок**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemextension.vb#1)]  
  
 В этом примере служба проекта SharePoint используется для записи сообщения в окна **Выходные данные** и **Список ошибок**.  Дополнительные сведения см. в разделе [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание расширения  
 Чтобы развернуть расширение, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  