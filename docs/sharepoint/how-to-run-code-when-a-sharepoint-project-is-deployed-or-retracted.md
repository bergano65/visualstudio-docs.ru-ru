---
title: Выполнения кода при развертывания или отзыва проекта SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e3f46ff9d2e83307f745180288e69839a0d336e
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401762"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Практическое руководство. Выполнения кода при развертывания или отзыва проекта SharePoint
  Если вы хотите выполнить дополнительные задачи после развертывания или отзыва проекта SharePoint, можно обрабатывать события, вызываемые с Visual Studio. Дополнительные сведения см. в разделе [SharePoint расширение упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Для выполнения кода при создании проекта SharePoint развертывания или отзыва

1. Создание расширения элемента проекта, расширение проекта или определение нового типа элемента проекта. Дополнительные сведения см. в следующих разделах:

   - [Практическое руководство. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Практическое руководство. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Практическое руководство. Определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. В расширении, доступ к <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта. Дополнительные сведения см. в разделе [Практическое руководство. Службе project SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> события службы проекта.

4. В событии обработчики, используют <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> параметра, чтобы получить сведения о текущем сеансе развертывания. Например, можно определить, какой проект находится в текущем сеансе развертывания и ли их развертывания или отзыва.

   В следующем примере кода показано, как обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> события в расширении проекта. Это расширение записывает дополнительное сообщение для **вывода** окно развертывания начале и конце для проекта SharePoint.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере требуются ссылки на следующие сборки:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Практическое руководство. Выполнения кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
