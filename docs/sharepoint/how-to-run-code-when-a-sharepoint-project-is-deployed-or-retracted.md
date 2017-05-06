---
title: "How to: Run Code When a SharePoint Project is Deployed or Retracted"
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
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Run Code When a SharePoint Project is Deployed or Retracted
  При необходимости выполнения дополнительных задач во время развертывания или отзыва проекта SharePoint можно обрабатывать события, вызываемые Visual Studio.  Дополнительные сведения см. в разделе [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### Выполнение кода во время развертывания или отзыва проекта SharePoint  
  
1.  Создайте расширение элемента проекта, расширение проекта или определение нового типа элемента проекта.  Дополнительные сведения см. в следующих разделах.  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  В расширении обратитесь к объекту <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  Дополнительные сведения см. в разделе [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Обработайте события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>службы проекта.  
  
4.  В обработчиках событий воспользуйтесь параметром <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> для получения сведений о текущем сеансе развертывания.  Например, можно определить какой проект находится в текущем сеансе развертывания, и развертывается ли он или отзывается.  
  
 В следующем примере кода показано, как использовать элементы <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> в расширении проекта.  Это расширение записывает дополнительное сообщение в окно **Выход** в начале и конце развертывания для проекта SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handleprojectdeploymentevents.vb#12)]  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание расширения  
 Чтобы развернуть расширение, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  