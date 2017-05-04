---
title: "How to: Add a Custom SharePoint Node to Server Explorer | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# How to: Add a Custom SharePoint Node to Server Explorer
  В узел **Подключения SharePoint** в **Обозревателе сервера** можно добавлять пользовательские узлы.  Это бывает удобно, если требуется отображать дополнительные компоненты SharePoint, которые не отображаются в **Обозревателе сервера** по умолчанию.  Дополнительные сведения см. в разделе [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Чтобы добавить пользовательский узел, сначала создайте класс, определяющий новый узел.  Затем создайте расширение, которое добавляет этот узел в качестве дочернего для имеющегося узла.  
  
### Определение нового узла  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  
  
4.  Добавьте следующие атрибуты к классу:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Этот атрибут позволяет Visual Studio находить и загружать пользовательскую реализацию <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Передайте конструктору этого атрибута тип <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>;  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  В определении узла этот атрибут задает идентификатор строки для нового узла.  Чтобы все узлы имели уникальные идентификаторы, рекомендуется использовать формат *название\_компании*.*имя\_узла*.  
  
5.  В текущей реализации метода <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> с помощью членов параметра *typeDefinition* настройте поведение нового узла.  Этот параметр представляет собой объект <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>, который предоставляет доступ к событиям, определенным в интерфейсе <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>.  
  
     В следующем примере кода демонстрируется определение нового узла.  В этом пример предполагается, что проект содержит в качестве внедренного ресурса значок с именем CustomChildNodeIcon.  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#6)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#6)]  
  
### Добавление нового узла в качестве дочернего для имеющегося узла  
  
1.  В проекте, содержащем определение нового узла, создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
2.  Добавьте в класс атрибут <xref:System.ComponentModel.Composition.ExportAttribute>.  Этот атрибут позволяет Visual Studio находить и загружать пользовательскую реализацию класса <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Передайте этому конструктору атрибута тип <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>;  
  
3.  Добавьте в класс атрибут <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  В расширении узла этот атрибут задает идентификатор строки для типа узла, который требуется расширить.  
  
     Чтобы указать предусмотренные в Visual Studio встроенные типы узлов, передайте одно из следующих значений перечисления конструктору атрибута.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes> — эти значения позволяют задать узлы подключения сайтов \(узлы, отображающие URL\-адрес сайта\), узлы сайтов и все другие родительские узлы в окне **Обозреватель решений**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes> – эти значения позволяют задать один из встроенных узлов, представляющих отдельный компонент на сайте SharePoint, например узел, представляющий список, поле или тип содержимого.  
  
4.  В реализации метода <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> обработайте событие <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> параметра <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>.  
  
5.  В обработчике событий <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> добавьте новый узел в коллекцию дочерних узлов объекта <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A>, предоставляемого параметром аргументов события.  
  
     В следующем примере кода показано добавление нового узла в качестве дочернего узла сайта SharePoint в **Обозревателе серверов**.  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#7)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#7)]  
  
## Полный пример  
 В следующем примере представлен полный код для определения простого узла и добавления его в качестве дочернего узла сайта SharePoint в **Обозревателе серверов**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#5)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#5)]  
  
## Компиляция кода  
 В этом пример предполагается, что проект содержит в качестве внедренного ресурса значок с именем CustomChildNodeIcon.  Для этого примера также требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## Развертывание расширения  
 Чтобы развернуть расширение **обозревателя сервера**, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться вместе с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  