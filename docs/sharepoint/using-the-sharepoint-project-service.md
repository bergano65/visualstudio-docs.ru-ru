---
title: Использование службы проектов SharePoint | Документация Майкрософт
description: Используйте службу проектов SharePoint для выполнения задач, связанных с системой проектов. Просмотр списка функций службы Project.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5366be3ed60da9225eaf10b19f58ccd77bffbb90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892194"
---
# <a name="use-the-sharepoint-project-service"></a>Использование службы проектов SharePoint
  Система проектов SharePoint включает службу Project, которую можно использовать для выполнения задач, относящихся к системе проектов. Служба Project — это объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.

 Доступ к службе Project SharePoint можно получить из любого расширения инструментов SharePoint. Доступ к ней также можно получить из других типов расширений Visual Studio, например из надстроек и пакетов VSPackages. Дополнительные сведения см. [в разделе как получить службу проекта SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Функции службы Project
 В следующей таблице перечислены задачи, которые можно выполнять с помощью службы Project SharePoint и используемый метод или свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> для выполнения каждой из задач.

|Задача|Используемый член|
|----------|-------------------|
|Доступ к любому проекту SharePoint, открытому в Visual Studio.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|
|Доступ ко всем доступным типам элементов проектов SharePoint (включая встроенные и пользовательские типы элементов проекта).|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|
|Доступ ко всем шагам развертывания, которые доступны для проектов SharePoint (включая встроенные и пользовательские шаги развертывания).|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|
|Доступ к событиям, возникающим, когда разработчик выполняет рефакторинг кода в проекте SharePoint.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|
|Выполните пользовательскую *команду SharePoint* , которая вызывает объектную модель сервера SharePoint. Дополнительные сведения о командах SharePoint см. в разделе [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|
|Преобразование типа из системы проектов SharePoint в тип из объектной модели автоматизации Visual Studio или объектной модели интеграции и наоборот. Дополнительные сведения см. в разделе [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Метод <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|
|Запись сообщений в окно **вывода** или **Список ошибок** окно в Visual Studio.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|
|Доступ к другим службам, доступным в Visual Studio.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|
|Получение пути к папке установки локального сайта SharePoint, который используется для отладки решения.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|
|Определение того, что именно установлено на компьютере: [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] или [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)].|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|
|Проверка компонента или пакета решения SharePoint.|Свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|

## <a name="see-also"></a>См. также раздел
- [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Как получить службу проекта SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Расширение средств SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Обзор модели программирования расширений инструментов SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Практическое руководство. Получение службы из объекта DTE](/previous-versions/bb166401(v=vs.140))