---
title: "Как: выполнение команды SharePoint | Документы Microsoft"
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
helpviewer_keywords: SharePoint commands [SharePoint development in Visual Studio], executing
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1cfe20d0cac50603265644fb48102ef22537631
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-execute-a-sharepoint-command"></a>Практическое руководство. Выполнение команды SharePoint
  Если вы хотите использовать в расширении инструментов SharePoint в серверную объектную модель, необходимо создать пользовательский *команда SharePoint* для вызова API. После определения команды и развернуть ее с помощью расширения средств SharePoint, расширение можно выполнить команду для вызова объектной модели сервера SharePoint. Чтобы выполнить команду, используйте один из методов ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта.  
  
 Дополнительные сведения о назначении команд SharePoint см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Для выполнения команды SharePoint  
  
1.  В расширения средств SharePoint, получите <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта. Способ получения <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объект зависит от типа расширения, которые вы создаете:  
  
    -   В расширении системы проектов SharePoint следует использовать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> свойства.  
  
         Дополнительные сведения о расширениях системы проектов см. в разделе [расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   В расширении **подключения SharePoint** узел в **обозревателя серверов**, используйте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> свойство. Для получения <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> , используйте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> свойство.  
  
         Дополнительные сведения о **обозревателя серверов** расширения, в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   В коде, который не является частью расширения инструментов SharePoint, например в мастере шаблонов проектов, используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> свойство.  
  
         Дополнительные сведения об обращении к службе проектов см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Вызовите один из методов ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта. Передайте имя команды, которую необходимо выполнить для первого аргумента метода ExecuteCommand. Если у команды есть настраиваемый параметр, передайте этот параметр во второй аргумент метода ExecuteCommand.  
  
     Имеется другой перегрузке ExecuteCommand для каждой из поддерживаемых сигнатур команды. В следующей таблице перечислены поддерживаемые сигнатуры и какую перегрузку следует использовать для каждой подписи.  
  
    |Команда подписи|ExecuteCommand перегрузку, чтобы использовать|  
    |-----------------------|------------------------------------|  
    |Команда имеет значение по умолчанию <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> параметр и не возвращает значений.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Команда имеет значение по умолчанию <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> параметром и возвращаемым значением.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Команда имеет два параметра (по умолчанию <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> параметры и пользовательские) и не возвращает значений.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Команда имеет два параметра и возвращаемого значения.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется использование <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> перегрузку, чтобы вызвать `Contoso.Commands.UpgradeSolution` команду, которая описана в [как: создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 `Execute` Показано в следующем примере метод является реализацией <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> метод <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> интерфейса в пользовательского шага развертывания. Этот код в контексте полного примера см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Обратите внимание, следующие сведения о вызове <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> метода:  
  
-   Первый параметр определяет команду, которую требуется вызвать. Эта строка соответствует значению, которое передается <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> при определении команды.  
  
-   Второй параметр-значение, передаваемое для настраиваемого параметра команды. В этом случае представляет полный путь к WSP-файла, которая обновляется на сайте SharePoint.  
  
-   Код не проходит неявный <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> в команду параметр. Этот параметр передается в команду автоматически при вызове команды из расширения системы проектов SharePoint или из расширения **подключения SharePoint** узел в **обозревателя серверов**. В других типах решений, например в мастере шаблонов проектов, который реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс, этот параметр является **null**.  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В этом примере требуется ссылка на сборку Microsoft.VisualStudio.SharePoint.  
  
## <a name="see-also"></a>См. также  
 [Обращение к объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Как: создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Пошаговое руководство. Расширение обозревателя сервера, так чтобы в нем отображались веб-части](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  