---
title: "How to: Extend a SharePoint Node in Server Explorer | Microsoft Docs"
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
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Extend a SharePoint Node in Server Explorer
  Пользователь может расширить вложенные узлы в узле **Подключения SharePoint** в **обозревателе сервера**.  Это удобно в случае необходимости добавить в существующий узел новые дочерние узлы, элементы контекстного меню или свойства.  Дополнительные сведения см. в разделе [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### Расширение узла SharePoint в обозревателе сервера  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
4.  Добавьте в класс атрибут <xref:System.ComponentModel.Composition.ExportAttribute>.  Этот атрибут позволяет Visual Studio находить и загружать пользовательскую реализацию класса <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Передайте этому конструктору атрибута тип <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>;  
  
5.  Добавьте в класс атрибут <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  Этот атрибут задает идентификатор строки для типа узла, который требуется расширить.  
  
     Чтобы указать предусмотренные в Visual Studio встроенные типы узлов, передайте одно из следующих значений перечисления конструктору атрибута.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes> — эти значения позволяют задать узлы подключения сайтов \(узлы, отображающие URL\-адрес сайта\), узлы сайтов и все другие родительские узлы в окне **Обозреватель решений**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes> – эти значения позволяют задать один из встроенных узлов, представляющих отдельный компонент на сайте SharePoint, например узел, представляющий список, поле или тип содержимого.  
  
6.  В текущей реализации метода <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> для добавления компонентов в узел используйте члены параметра *nodeType*.  Этот параметр представляет собой объект <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>, который предоставляет доступ к событиям, определенным в интерфейсе <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>.  Например, можно обработать следующие события.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> – это событие обрабатывается для добавления новых дочерних узлов в определенный узел.  Дополнительные сведения см. в разделе [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested> – это событие обрабатывается для добавления в узел настраиваемого пункта контекстного меню.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested> – это событие обрабатывается для добавления настраиваемых свойств в определенный узел.  Это свойство отображается в окне **Свойства** при выборе узла.  
  
## Пример  
 В следующем примере кода демонстрируется создание двух различных типов расширений узла.  
  
-   Расширение, добавляющее пункт контекстного меню для узлов сайта SharePoint.  При выборе этого пункта меню отображается имя выбранного узла.  
  
-   Расширение, добавляющее настраиваемое свойство с именем **ContosoExampleProperty** в каждый узел, представляющий поле с именем **Основная часть**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextension.vb#9)]  
  
 Это расширение добавляет для узлов редактируемое свойство строкового типа.  Кроме того, можно создать настраиваемые свойства, отображающие полученные с сервера SharePoint данные, которые доступны только для чтения.  Пример, в котором показано, как это сделать, см. в разделе [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## Развертывание расширения  
 Чтобы развернуть расширение **обозревателя сервера**, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться вместе с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  