---
title: "Как: обработка конфликтов развертывания | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: c3bbd5bc7d69fbc48d2c754151a3ec6b5fcb612c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-handle-deployment-conflicts"></a>Практическое руководство. Обработка конфликтов развертывания
  Можно предоставить свой собственный код для обработки конфликтов развертывания для элемента проекта SharePoint. Например можно предположить, уже существует в месте развертывания все файлы в текущем элементе проекта и затем удалить существующие файлы перед развертыванием элемента текущего проекта. Дополнительные сведения о конфликтах развертывания см. в разделе [расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-handle-a-deployment-conflict"></a>Для обработки конфликтов развертывания  
  
1.  Создание расширения элемента проекта, расширение проекта или определение нового типа элемента проекта. Дополнительные сведения см. в следующих разделах:  
  
    -   [Практическое руководство. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Практическое руководство. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Практическое руководство. Определение типа элементов проектов SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  В модуле обработки <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> объекта (в расширение элемента проекта или проекта расширения) или <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> объекта (в определении типа элемента проекта).  
  
3.  В обработчике событий определите, является конфликт между развертываемый элемент проекта и развернутое решение на сайте SharePoint, на основе критериев, которые применяются к вашему сценарию. Можно использовать <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> параметра аргументов событий для анализа элемент проекта, который выполняется развертывание, а также анализировать файлы в расположении развертывания путем вызова команды SharePoint, которая определяет для этой цели.  
  
     Для многих типов конфликтов сначала можно определить, какой шаг развертывания выполняется. Это можно сделать с помощью <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> свойства параметра аргументов события. Несмотря на то, что обычно имеет смысл для обнаружения конфликтов во время встроенного <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> шаг развертывания, вы можете проверить наличие конфликтов во время любой шаг развертывания.  
  
4.  Если существует конфликт, используйте <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> метод <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> свойств аргументов события для создания нового <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> объекта. Этот объект представляет конфликт развертывания. При вызове <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> метода, также укажите метод, вызываемый для разрешения конфликта.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется базовый процесс для обработки конфликтов развертывания в расширение элемента проекта для элементов проекта определения списка. Для обработки конфликтов развертывания для другого типа элемента проекта, передайте другую строку для <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Дополнительные сведения см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
 Для простоты <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> обработчик событий в этом примере предполагается, что существует конфликт в развертывании (т. е. он всегда добавляет новый <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> объекта) и `Resolve` метод просто возвращает **true** указывает, что конфликт разрешен. В реальном сценарии вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> обработчик событий должен сначала определить, если существует конфликт между файлом в элементе текущего проекта и файл в расположении развертывания, а затем добавьте <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> объекта, если существует конфликт. Например, можно использовать `e.ProjectItem.Files` свойство в обработчике событий для анализа файлов в элемент проекта и может вызывать команду SharePoint, чтобы анализировать файлы в расположении развертывания. Аналогичным образом в реальном сценарии `Resolve` метод может вызывать команду SharePoint для разрешения конфликта на сайте SharePoint. Дополнительные сведения о создании команд SharePoint см. в разделе [как: создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Как: выполнения кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Практическое руководство. Создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  