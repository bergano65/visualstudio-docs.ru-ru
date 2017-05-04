---
title: "How to: Execute a SharePoint Command | Microsoft Docs"
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
  - "SharePoint commands [SharePoint development in Visual Studio], executing"
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# How to: Execute a SharePoint Command
  Если в расширениях средств SharePoint требуется использовать серверную объектную модель, необходимо создать для вызова API настраиваемую *команду SharePoint*.  После определения команды и развертывания ее с помощью расширения средств SharePoint расширение может выполнять команду для вызова объектной модели сервера SharePoint.  Для выполнения команды воспользуйтесь одним из методов ExecuteCommand объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  
  
 Дополнительные сведения о командах SharePoint см. в разделе [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### Выполнение команды SharePoint  
  
1.  Получите объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> в расширении средств SharePoint.  Способ получения объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> зависит от типа создаваемого расширения.  
  
    -   В расширении системы проектов SharePoint следует использовать свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A>.  
  
         Дополнительные сведения о расширениях системы проектов см. в разделе [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   В расширении узла **Подключения SharePoint** в **обозревателе серверов** следует использовать свойство <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A>.  Чтобы получить объект <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext>, используйте свойство <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A>.  
  
         Дополнительные сведения о расширениях **обозревателя серверов** см. в разделе [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   В коде, который не является частью расширения средств SharePoint, например в мастере шаблонов проектов, следует использовать свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.  
  
         Дополнительные сведения об обращении к службе проектов см. в разделе [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Вызовите один из методов ExecuteCommand объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  Передайте в первый аргумент метода ExecuteCommand имя команды, которую необходимо выполнить.  Если у команды есть настраиваемый параметр, передайте этот параметр во второй аргумент метода ExecuteCommand.  
  
     Для каждой из поддерживаемых сигнатур команды имеется отдельная перегруженная версия метода ExecuteCommand.  В следующей таблице перечислены поддерживаемые сигнатуры и соответствующие перегруженные методы.  
  
    |Сигнатура команды|Используемая перегруженная версия ExecuteCommand|  
    |-----------------------|------------------------------------------------------|  
    |У команды есть только заданный по умолчанию параметр <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> и отсутствует возвращаемое значение.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |У команды есть только заданный по умолчанию параметр <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> и возвращаемое значение.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |У команды есть два параметра \(параметр <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>, используемый по умолчанию, и пользовательский параметр\), а также возвращаемое значение.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |У команды есть два параметра и возвращаемое значение.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## Пример  
 В следующем примере кода показано, как с помощью перегруженной версии метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> вызвать команду `Contoso.Commands.UpgradeSolution`, описанную в разделе [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#6)]  
  
 Продемонстрированный в данном примере метод `Execute` является реализацией метода <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> интерфейса <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> на настраиваемом этапе развертывания.  Данный код в контексте полного примера см. в раздел [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 При вызове метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> необходимо учитывать следующие особенности.  
  
-   Первый параметр определяет команду, которую необходимо вызвать.  Эта строка соответствует значению, переданному атрибуту <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> при определении команды.  
  
-   Второй параметр представляет собой значение, которое необходимо передать команде в качестве второго настраиваемого параметра.  В данном случае это полный путь к WSP\-файлу, обновляемому до сайта SharePoint.  
  
-   Этот код не передает команде неявный параметр <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>.  Данный параметр передается в команду автоматически при вызове команды из расширения системы проектов SharePoint или из расширения узла **Подключения SharePoint** в **обозревателе серверов**.  В решениях других типов, например в мастере шаблонов проектов, реализующем интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, этот параметр имеет значение **null**.  
  
## Компиляция кода  
 В этом примере необходима ссылка на сборку Microsoft.VisualStudio.SharePoint.  
  
## См. также  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  