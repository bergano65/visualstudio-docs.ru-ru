---
title: "Как: выполнения кода при проекта SharePoint является развертывания или отзыва | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b452d28b1fc8173435b4de993561b59a680b0fed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Практическое руководство. Выполнение кода во время развертывания или отзыва проекта SharePoint
  Если требуется выполнить дополнительные задачи, при развертывания или отзыва проекта SharePoint, можно обрабатывать события, вызываемые Visual Studio. Дополнительные сведения см. в разделе [расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Для выполнения кода, когда проект SharePoint развертывания или отзыва  
  
1.  Создание расширения элемента проекта, расширение проекта или определение нового типа элемента проекта. Дополнительные сведения см. в следующих разделах:  
  
    -   [Практическое руководство. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Практическое руководство. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Практическое руководство. Определение типа элементов проектов SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  В расширении, доступ к <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта. Дополнительные сведения см. в разделе [как: доступ к службе Project SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> события службы проекта.  
  
4.  В случае использования обработчиков, <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> параметр, чтобы получить сведения о текущем сеансе развертывания. Например, можно определить, какой проект находится в текущем сеансе развертывания и выполняется ли развертывания или отзыва.  
  
 В следующем примере кода показано, как обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> события в расширении проекта. Это расширение записывает дополнительное сообщение для **вывода** окно при запуске и конце развертывания для проекта SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Практическое руководство. Запуск кода после выполнения этапов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  