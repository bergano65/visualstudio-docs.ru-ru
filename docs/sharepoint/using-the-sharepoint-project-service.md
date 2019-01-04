---
title: Использование службы проектов SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a8416d38629c8970e9cc90e0d873138970b16258
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875823"
---
# <a name="use-the-sharepoint-project-service"></a>Использование службы проектов SharePoint
  Система проектов SharePoint включает службу Project, которую можно использовать для выполнения задач, относящихся к системе проектов. Служба Project — это объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  
  
 Доступ к службе Project SharePoint можно получить из любого расширения инструментов SharePoint. Доступ к ней также можно получить из других типов расширений Visual Studio, например из надстроек и пакетов VSPackages. Дополнительные сведения см. в разделе [Как Службе project SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## <a name="project-service-features"></a>Возможности службы Project
 В следующей таблице перечислены задачи, которые можно выполнять с помощью службы Project SharePoint и используемый метод или свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> для выполнения каждой из задач.  
  
|Задача|Используемый член|  
|----------|-------------------|  
|Доступ к любому проекту SharePoint, открытому в Visual Studio.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|  
|Доступ ко всем доступным типам элементов проектов SharePoint (включая встроенные и пользовательские типы элементов проекта).|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|  
|Доступ ко всем шагам развертывания, которые доступны для проектов SharePoint (включая встроенные и пользовательские шаги развертывания).|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|  
|Доступ к событиям, возникающим, когда разработчик выполняет рефакторинг кода в проекте SharePoint.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|  
|Выполнение пользовательской *команды SharePoint* , обращающейся к объектной модели сервера SharePoint. Дополнительные сведения о командах SharePoint см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|  
|Преобразование типа из системы проектов SharePoint в тип из объектной модели автоматизации Visual Studio или объектной модели интеграции и наоборот. Дополнительные сведения см. в разделе [преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Метод <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|  
|Записывать сообщения в **вывода** окна или **список ошибок** окно в Visual Studio.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|  
|Доступ к другим службам, доступным в Visual Studio.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|  
|Получение пути к папке установки локального сайта SharePoint, который используется для отладки решения.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|  
|Определение того, что именно установлено на компьютере: [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] или [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)].|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|  
|Проверка компонента или пакета решения SharePoint.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|  
  
## <a name="see-also"></a>См. также
 [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Практическое руководство. Получить службы проектов SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Расширения инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Обзор модели программирования SharePoint средств расширения](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Практическое руководство. Доступ к службе из объекта DTE](https://msdn.microsoft.com/library/bb166401.aspx)  
