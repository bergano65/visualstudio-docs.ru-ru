---
title: Практическое руководство. Службе SharePoint Project | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce7b6705fcbafaf713faed6f937fcfa29bd013d6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597379"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Практическое руководство. Получить службы проектов SharePoint
  Доступны службы проектов SharePoint в следующих типов решений:

-   Расширение системы проектов SharePoint, например расширение проекта, расширения элемента проекта или определении типа элемента проекта. Дополнительные сведения об этих типах расширений см. в разделе [расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

-   Расширение **подключения SharePoint** узел в **обозревателя серверов**. Дополнительные сведения об этих типах расширений см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

-   Другой тип расширения Visual Studio, например VSPackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Обращение к службе в расширениях системы проектов
 В любое расширение системы проектов SharePoint, можно получить доступ к службе проектов с помощью <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объекта.

 Служба проекта можно также получить с помощью следующих процедур.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Обращение к службе в расширении проекта

1.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейсом, найдите <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метод.

2.  Используйте *projectService* параметр для доступа к службе.

     В следующем примере кода демонстрируется использование службы проектов для записи сообщения в **вывода** окна и **список ошибок** окно в расширении простого проекта.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     Дополнительные сведения о создании расширений проекта см. в разделе [как: Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Обращение к службе в расширение элемента проекта

1.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> интерфейсом, найдите <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метод.

2.  Используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> *свойство* параметр обращение к службе.

     В следующем примере кода демонстрируется использование службы проектов для записи сообщения в **вывода** окна и **список ошибок** окно в простое расширение **определение списка** элемент проекта.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     Дополнительные сведения о создании расширений элемента проекта, см. в разделе [как: Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Обращение к службе в определении типа элемента проекта

1.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейсом, найдите <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод.

2.  Используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> свойство *typeDefinition* параметр обращение к службе.

     В следующем примере кода демонстрируется использование службы проектов для записи сообщения в **вывода** окна и **список ошибок** окно в определении типа элемента простого проекта.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     Дополнительные сведения об определении типов элементов проектов см. в разделе [как: Определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Обращение к службе в обозревателе серверов расширений
 В расширении **подключения SharePoint** узел в **обозревателя серверов**, доступ к службе проектов с помощью <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> объекта.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Обращение к службе в расширении обозревателя серверов

1.  Получить <xref:System.IServiceProvider> объекта из <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> объекта расширения.

2.  Используйте <xref:System.IServiceProvider.GetService%2A> метод для запроса <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта.

     В следующем примере кода демонстрируется использование службы проектов для записи сообщения в **вывода** окна и **список ошибок** окно из контекстного меню, расширения для списка узлов в **Обозреватель серверов**.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     Дополнительные сведения о расширении **подключения SharePoint** узел в **обозревателя серверов**, см. в разделе [как: Расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Обращение к службе в другими расширениями Visual Studio
 Вы можете получить проект службы в VSPackage или в любое расширение Visual Studio, имеющей доступ к <xref:EnvDTE80.DTE2> объектов в объектной модели автоматизации, такие как мастер шаблонов проектов, который реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс.

 В пакете VSPackage, вы можете запросить <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта с помощью одного из следующих методов:

- <xref:System.IServiceProvider.GetService%2A> Метод управляемого пакета VSPackage, который является производным от <xref:Microsoft.VisualStudio.Shell.Package> класса. Дополнительные сведения см. в разделе [Как Доступ к службе](../extensibility/how-to-get-a-service.md).

- Статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод. Дополнительные сведения см. в разделе [использование GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  В расширении Visual Studio, имеющей доступ к <xref:EnvDTE80.DTE2> объект, вы можете запросить <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта с помощью <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> метод <xref:Microsoft.VisualStudio.Shell.ServiceProvider> объекта. Дополнительные сведения см. в разделе [Получение службы из объекта DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>См. также
- [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Практическое руководство. Получение службы](../extensibility/how-to-get-a-service.md)
- [Практическое руководство. Использование мастеров для шаблонов проектов](../extensibility/how-to-use-wizards-with-project-templates.md)
