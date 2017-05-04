---
title: "How to: Get Data for a Built-In SharePoint Node in Server Explorer | Microsoft Docs"
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
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Get Data for a Built-In SharePoint Node in Server Explorer
  Для каждого узла SharePoint, встроенного в **Обозреватель сервера**, можно получить данные по указанному компоненту SharePoint, которые представлены в узле.  Дополнительные сведения см. в разделе [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## Пример  
 В следующем примере кода показано получение данных по указанному списку SharePoint, который представлен в узле списка в **Обозревателе сервера**.  По умолчанию узлы списка содержат пункт контекстного меню **Просмотр в обозревателе**, которым можно воспользоваться, чтобы открыть список в веб\-браузере.  В данном примере осуществляется расширение узлов списка посредством добавления пункта контекстного меню **Просмотр в Visual Studio**, который позволяет открыть списки непосредственно в Visual Studio.  Код обращается к данным списка для узла, чтобы получить URL\-адрес списка, открываемого в Visual Studio.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#10)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#10)]  
  
 В примере используется служба проекта SharePoint для получения объекта <xref:EnvDTE.DTE>, используемого для открытия списков в Visual Studio.  Дополнительные сведения о службе проекта SharePoint см. в разделе [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Дополнительные сведения об основных задачах для создания расширения узла SharePoint см. в разделе [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## Развертывание расширения  
 Чтобы развернуть расширение **обозревателя сервера**, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться вместе с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  