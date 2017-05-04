---
title: "How to: Handle Deployment Conflicts | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Handle Deployment Conflicts
  Можно самостоятельно создать код для обработки конфликтов развертывания в элементе проекта SharePoint.  Например, можно определить, существуют ли уже какие\-либо файлы элемента текущего проекта в расположении развертывания, и удалить существующие файлы перед развертыванием элемента текущего проекта.  Дополнительные сведения о конфликтах при развертывании см. в разделе [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### Обработка конфликтов развертывания  
  
1.  Создайте расширение элемента проекта, расширение проекта или определение нового типа элемента проекта.  Дополнительные сведения см. в следующих разделах.  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  В расширении обработайте событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> \(в расширении элемента проекта или расширении проекта\) либо объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> \(в определении нового типа элемента проекта\).  
  
3.  В обработчике событий поместите код, определяющий, конфликтует ли развертываемый элемент проекта с развернутым решением на сайте SharePoint, по критериям, применимым к данному сценарию.  С помощью свойства <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> параметра аргументов события можно проанализировать развертываемый элемент проекта, а файлы в расположении развертывания можно проанализировать с помощью команды SharePoint, определенной для этой цели.  
  
     При обработке большинства типов конфликтов сначала требуется определить, какой шаг развертывания выполняется.  Это можно сделать при помощи свойства <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> параметра аргументов события.  Как правило, имеет смысл проверять наличие конфликтов во время встроенного шага развертывания <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution>, однако такую проверку можно выполнять на любом шаге развертывания.  
  
4.  При наличии конфликта с помощью метода <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> свойства <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> аргументов события создайте новый объект <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>.  Этот объект представляет конфликт развертывания.  При вызове метода <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> также укажите метод, вызываемый для разрешения конфликта.  
  
## Пример  
 В следующем примере кода показан простейший процесс обработки конфликтов развертывания в расширении элемента проекта для элементов проекта определения списка.  Для обработки конфликтов развертывания в другом типе элемента проекта укажите другую строку в атрибуте <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Дополнительные сведения см. в разделе [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
 Для простоты в данном примере обработчик событий <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> предполагает, что конфликт в развертывании существует \(т. е. он всегда добавляет новый объект <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>\), а метод `Resolve` просто возвращает значение **true**, указывающее, что конфликт разрешен.  В реальной практике обработчик событий <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> сначала определяет, существует ли конфликт между файлом в элементе текущего проекта и файлом в расположении развертывания, затем добавляет объект <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> только при наличии конфликта.  Например, с помощью свойства `e.ProjectItem.Files` обработчика событий можно анализировать файлы элемента проекта, а с помощью вызова команды SharePoint — анализировать файлы в расположении развертывания.  Аналогичным образом, в реальной практике метод `Resolve` может вызывать команду SharePoint для разрешения конфликта на сайте SharePoint.  Дополнительные сведения о создании команд SharePoint см. в разделе [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/cs/extension/deploymentconflictextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/vb/extension/deploymentconflictextension.vb#1)]  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание расширения  
 Чтобы развернуть расширение, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  