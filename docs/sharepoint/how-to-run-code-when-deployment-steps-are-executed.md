---
title: Как выполнить Выполнения кода при руководство | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 62ab9019eb9722baca523aeff00b4ed511039497
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883260"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Как выполнить Выполнения кода при выполнении шагов развертывания
  Если вы хотите выполнить дополнительные задачи для шага развертывания в проекте SharePoint, можно обрабатывать события, вызываемые элементами проекта SharePoint, до и после Visual Studio выполняет каждый шаг развертывания. Дополнительные сведения см. в разделе [расширение SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Для выполнения кода при выполнении шагов развертывания  
  
1.  Создание расширения элемента проекта, расширение проекта или определение нового типа элемента проекта. Дополнительные сведения см. в следующих разделах:  
  
    -   [Практическое руководство. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Практическое руководство. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Практическое руководство. Определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  В расширении, обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> объекта (в расширение элемента проекта или расширения проекта) или <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> объект (в определение нового типа элемента проекта).  
  
3.  В событии обработчики, используют <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> и <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> для получения сведений о шаге развертывания. Например, можно определить, какой шаг развертывания выполняется и ли решение находится в процессе развертывания или отзыва.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> события в расширение элемента проекта экземпляра списка. Это расширение записывает дополнительное сообщение для **вывода** окно, когда Visual Studio повторно использует пул приложений при развертывании и отзыве решения.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 В этом примере требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также
 [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Практическое руководство. Выполнения кода при развертывания или отзыва проекта SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
