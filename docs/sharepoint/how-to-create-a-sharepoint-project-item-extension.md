---
title: 'Как: создание расширения элемента проекта SharePoint | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b556bd47f35bf9c346159690925f854587e1178
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Практическое руководство. Создание расширения элемента проекта SharePoint
  Создание расширения элемента проекта, если вы хотите добавить функциональные возможности для элемента проекта SharePoint, который уже установлен в Visual Studio. Дополнительные сведения см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
### <a name="to-create-a-project-item-extension"></a>Создание расширения элемента проекта  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  
  
4.  Добавьте в класс следующие атрибуты:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Этот атрибут позволяет Visual Studio находить и загружать вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> тип в конструктор атрибута.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. В расширение элемента проекта этот атрибут определяет элемент проекта, который требуется расширить. Передайте идентификатор элемента проекта в конструктор атрибута. Список идентификаторов элементов проекта, которые входят в состав Visual Studio см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метод помощью членов *изменить* параметра для определения поведения расширения. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> объект, предоставляющий доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> интерфейсов. Для доступа к экземпляр типа элемента проекта, расширении, обработку <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> события, такие как <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется создание простого расширения для элемента проекта приемника событий. Каждый раз пользователь добавляет элемент проекта приемника событий в проект SharePoint, это расширение записывает сообщение в **вывода** окна и **список ошибок** окна.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 В этом примере используется служба проекта SharePoint для записи сообщения для **вывода** окна и **список ошибок** окна. Дополнительные сведения см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Пошаговое руководство. Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  