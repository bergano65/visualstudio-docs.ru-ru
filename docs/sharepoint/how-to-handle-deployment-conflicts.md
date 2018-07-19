---
title: 'Практическое: обработка конфликтов развертывания | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d7c30a7c634c30c9fe3e92ef988d7d8fc043cf6b
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119869"
---
# <a name="how-to-handle-deployment-conflicts"></a>Практическое: обработка конфликтов развертывания
  Можно предоставить собственный код для обработки конфликтов развертывания для элемента проекта SharePoint. Например может определить, уже существует в месте развертывания все файлы в текущем элементе проекта и затем удалить существующие файлы перед развертыванием элемента текущего проекта. Дополнительные сведения о конфликтах развертывания см. в разделе [расширение SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-handle-a-deployment-conflict"></a>Для обработки конфликтов развертывания  
  
1.  Создание расширения элемента проекта, расширение проекта или определение нового типа элемента проекта. Дополнительные сведения см. в следующих разделах:  
  
    -   [Практическое: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Практическое: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  В расширении, обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> объекта (в расширение элемента проекта или расширения проекта) или <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> объект (в определение нового типа элемента проекта).  
  
3.  В обработчике событий определите, существует ли конфликт между элемент проекта, который развертывается и развернутого решения на сайте SharePoint, на основе критериев, которые применяются к вашему сценарию. Можно использовать <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> параметра аргументы события для анализа, который развертывается элемент проекта, а также можно анализировать файлы в расположении развертывания путем вызова команды SharePoint, вы определяете для этой цели.  
  
     Для многих типов конфликтов сначала можно определить, какой шаг развертывания выполняется. Это можно сделать с помощью <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> свойства параметра аргументов события. Несмотря на то, что обычно имеет смысл для обнаружения конфликтов во время встроенного <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> шаг развертывания, вы можете проверить наличие конфликтов во время выполнения любого шага развертывания.  
  
4.  Если существует конфликт, используйте <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> метод <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> свойство аргументов события для создания нового <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> объекта. Этот объект представляет конфликт развертывания. При вызове <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> метода, также укажите метод, вызываемый для разрешения конфликта.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется базовый процесс для обработки конфликтов развертывания в расширение элемента проекта для элементов проекта определения списка. Для обработки конфликтов развертывания для другого типа элемента проекта, передайте другую строку для <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Дополнительные сведения см. в разделе [элементы проекта SharePoint, расширить](../sharepoint/extending-sharepoint-project-items.md).  
  
 Для простоты <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> обработчик событий в этом примере предполагается, что существует конфликт развертывания (т. е. он всегда добавляет новый <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> объекта) и `Resolve` метод просто возвращает **true** указывает, что конфликт был разрешен. В реальном сценарии вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> обработчик событий будет сначала определить, если существует конфликт между файлом в текущий элемент проекта и файл в расположении развертывания, а затем добавьте <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> объекта, если существует конфликт. Например, можно использовать `e.ProjectItem.Files` свойство в обработчике событий для анализа файлов в элемент проекта, а также может вызывать команду SharePoint, чтобы проанализировать файлы в папке развертывания. Аналогичным образом, в реальном сценарии `Resolve` метода может вызывать команду SharePoint для разрешения конфликта на сайте SharePoint. Дополнительные сведения о создании команд SharePoint см. в разделе [как: создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 В этом примере требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также
 [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Практическое: выполнения кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Практическое: создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
