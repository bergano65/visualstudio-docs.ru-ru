---
title: Практическое руководство. Выполнение команды SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f5c285e71179c5dd59fad0357dbf71ee4b32f9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813893"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Практическое руководство. Выполнение команды SharePoint
  Если вы хотите использовать серверную объектную модель в расширения инструментов SharePoint, необходимо создать пользовательский *команды SharePoint* для вызова API. После определения команды и развернуть его с помощью расширения средств SharePoint, расширение можно выполнить команду для вызова объектной модели SharePoint server. Чтобы выполнить команду, используйте один из методов ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта.

 Дополнительные сведения о назначении команд SharePoint см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Для выполнения команды SharePoint

1. В расширения средств SharePoint, получают <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта. Способ получения <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объект зависит от типа расширения, вы создаете:

    - В расширении системы проектов SharePoint, использовать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> свойство.

         Дополнительные сведения о расширениях системы проектов, см. в разделе [расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

    - В расширении **подключения SharePoint** узел в **обозревателя серверов**, используйте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> свойство. Чтобы получить <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> , используйте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> свойство.

         Дополнительные сведения о **обозревателя серверов** расширения, см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - В коде, который не является частью расширения средств SharePoint, такие как мастер шаблонов проектов, используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> свойство.

         Дополнительные сведения о получении службы проекта см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

2. Вызовите один из методов ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта. Передайте имя команды, которые вы хотите выполнить, чтобы первый аргумент метода ExecuteCommand. Если у команды есть настраиваемый параметр, передайте этот параметр, чтобы второй аргумент метода ExecuteCommand.

     Нет другую перегрузку ExecuteCommand для каждой поддерживаемой команды подписи. Ниже перечислены поддерживаемые сигнатуры и какая перегруженная версия будет использовать для каждой подписи.

    |Команда подписи|Перегрузка ExecuteCommand для использования|
    |-----------------------|------------------------------------|
    |Команда имеет значение по умолчанию <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> параметров и возвращаемых значений.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Команда имеет значение по умолчанию <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> параметром и возвращаемым значением.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Команда имеет два параметра (значение по умолчанию <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> параметр и пользовательский параметр) и не возвращает значение.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Команда имеет два параметра и возвращаемого значения.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Пример
 В следующем примере кода демонстрируется использование <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> перегрузки для вызова `Contoso.Commands.UpgradeSolution` команду, которая описана в [как: Создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 `Execute` Показано в следующем примере метод представляет собой реализацию <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> метод <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> интерфейс в пользовательский шаг развертывания. Этот код в контексте большего примера, см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Обратите внимание на следующее о вызове <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> метод:

- Первый параметр определяет команду, необходимо вызвать. Эта строка соответствует значению, передаваемый <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> при определении команды.

- Второй параметр имеет значение, которое вы хотите передать для настраиваемого параметра команды. В данном случае это полный путь к *.wsp* файла, которое обновляется на сайте SharePoint.

- Код, не выполняет неявное <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> команду параметр. Этот параметр передается в команду автоматически при вызове команды из расширения системы проектов SharePoint или расширением **подключения SharePoint** узел в **обозревателя серверов**. В других типах решений, например мастер шаблонов проектов, который реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс, этот параметр является **null**.

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере требуется ссылка на сборку Microsoft.VisualStudio.SharePoint.

## <a name="see-also"></a>См. также
- [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Практическое руководство. Создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
