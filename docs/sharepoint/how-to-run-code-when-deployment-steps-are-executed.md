---
title: "Как: выполнения кода при выполнении шагов развертывания | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: ad603c9f303cd5bf2b3dc317efddd2694e10a867
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Практическое руководство. Запуск кода после выполнения шагов развертывания
  Если вы хотите выполнить дополнительные задачи для шага развертывания проекта SharePoint, может обрабатывать события, вызываемые элементами проекта SharePoint, до и после выполнения каждого шага развертывания, в Visual Studio. Дополнительные сведения см. в разделе [расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Для выполнения кода при выполнении шагов развертывания  
  
1.  Создание расширения элемента проекта, расширение проекта или определение нового типа элемента проекта. Дополнительные сведения см. в следующих разделах:  
  
    -   [Практическое руководство. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Практическое руководство. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Практическое руководство. Определение типа элементов проектов SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  В модуле обработки <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> объекта (в расширение элемента проекта или проекта расширения) или <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> объекта (в определении типа элемента проекта).  
  
3.  В случае использования обработчиков, <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> и <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> для получения сведений о шаге развертывания. Например, можно определить, какой шаг развертывания выполняется и ли решение находится в процессе развертывания или отзыва.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> события в расширение элемента проекта экземпляра списка. Это расширение записывает дополнительное сообщение для **вывода** окна, когда Visual Studio повторно использует пул приложений при развертывании и отзыве решения.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Практическое руководство. Выполнение кода во время развертывания или отзыва проекта SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  