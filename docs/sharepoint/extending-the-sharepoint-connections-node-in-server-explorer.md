---
title: "Extending the SharePoint Connections Node in Server Explorer | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Extending the SharePoint Connections Node in Server Explorer
  В Visual Studio можно подключиться к локальному сайтам SharePoint на компьютере разработчика, используя узла **Подключения SharePoint** в окне**Обозреватель серверов**.  Этот узел содержит многие компоненты локальных сайтов SharePoint в иерархическом древовидном представлении.  Например, он позволяет просматривать списки, библиотеки документов и типы содержимого на локальных сайтах. Дополнительные сведения о подключении к локальным сайтам SharePoint с помощью **обозревателя серверов** см. в разделе [Просмотр подключений SharePoint с помощью обозревателя серверов](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Можно раскрыть узел **Подключения SharePoint**, создав расширения для существующих узлов или создав пользовательский тип узла и добавив его в иерархию узлов.  
  
## Задачи для расширения узла подключений SharePoint  
 Чтобы расширить существующий узел, нужно создать расширение Visual Studio, реализующее интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  При расширении узла можно добавлять в узел функциональные возможности, например пользовательские пункты контекстного меню или пользовательские свойства.  Дополнительные сведения см. в разделе [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Чтобы создать пользовательский тип узла, нужно создать расширение Visual Studio, реализующее интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Пользовательский узел следует создавать, если требуется отображать компоненты сайтов SharePoint, которые не отображаются в **обозревателе серверов** по умолчанию.  Например, в **обозревателе серверов** по умолчанию не отображается коллекция веб\-частей сайта SharePoint, однако для ее отображения можно добавить пользовательский узел.  Дополнительные сведения см. в разделах [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) и [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Добавление пользовательских свойств в узлы  
 При расширении узла или создании пользовательского типа узла можно добавить в узел пользовательские свойства.  Это свойство отображается в окне **Свойства** при выборе узла.  
  
 В узел можно добавить два типа пользовательских свойств.  
  
-   Свойства, отображающие набор доступных только для чтения данных с сайта SharePoint.  Эти данные характеризуют компонент SharePoint, представленный узлом.  Соответствующее пошаговое руководство см. в разделе [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Свойства, отображающие пользовательские данные о чтении и записи.  Пример кода, в котором показано, как это сделать, см. в разделе [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Получение данных для встроенных узлов  
 Все встроенные узлы, которые предоставляются Visual Studio, содержат определенные данные о компоненте SharePoint, которые они представляют.  Например, узел, представляющий список на сайте SharePoint, предоставляет некоторые данные об этом списке, такие как название и URL\-адрес представления списка по умолчанию.  
  
 Для получения доступа к этим данным необходимо извлечь объект данных из свойства <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>, который представляет нужный пользователю узел.  Тип объекта данных зависит от типа узла.  
  
 В следующем примере кода показано получение объекта данных для узла списка.  Данный пример в контексте полного примера см. в разделе [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#11)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#11)]  
  
 В следующей таблице приводится список типов объектов данных для каждого типа встроенного узла.  
  
|Тип узла|Тип объекта данных|  
|--------------|------------------------|  
|Узел сайта SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Тип содержимого|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Функция|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Поле|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Шаблон списка|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Представление списка \(Microsoft.SharePoint.SPView\)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Связывание рабочих процессов|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Шаблон рабочего процесса|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Дополнительные сведения об использовании свойства <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> см. в разделе [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## См. также  
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Просмотр подключений SharePoint с помощью обозревателя серверов](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  