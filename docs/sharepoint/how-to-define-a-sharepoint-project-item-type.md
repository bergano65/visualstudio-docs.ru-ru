---
title: "Как: определить тип элемента проекта SharePoint | Документы Microsoft"
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
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fb19c360f19890c7e9c116ad721dd99ef633d47a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Практическое руководство. Определение типа элементов проектов SharePoint
  Определите тип элемента проекта для создания пользовательского элемента проекта SharePoint. Дополнительные сведения см. в разделе [определение типов элементов проектов настраиваемый SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### <a name="to-define-a-project-item-type"></a>Чтобы определить тип элемента проекта  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  
  
4.  Добавьте в класс следующие атрибуты:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Этот атрибут позволяет Visual Studio находить и загружать вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> тип в конструктор атрибута.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. В определении типа элемента проекта этот атрибут задает идентификатор строки для нового элемента проекта. Мы рекомендуем использовать формат *название компании*. *имя функции* для того, чтобы гарантировать, что все элементы проекта иметь уникальное имя.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Этот атрибут задает значок, отображаемый для этого элемента проекта в **обозревателе решений**. Этот атрибут является необязательным. Если не применить его к классу, Visual Studio отображает значок по умолчанию для элемента проекта. Если присвоить этому атрибуту передайте полное имя значка или растрового изображения, внедренного в сборку.  
  
5.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод помощью членов *projectItemTypeDefinition* параметра для определения поведения типа элемента проекта. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> объект, предоставляющий доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> интерфейсов. Чтобы получить доступ к определенному экземпляру типа элемента проекта, необходимо обработать событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> события, такие как <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется определение простого типа проектного элемента. Этот тип элемента проекта записывает сообщение в **вывода** окна и **список ошибок** окна, когда пользователь добавляет этого типа элемента проекта в проект.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 В этом примере используется служба проекта SharePoint для записи сообщения для **вывода** окна и **список ошибок** окна. Дополнительные сведения см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Развертывание элемента проекта  
 Чтобы включить другие разработчики также могли использовать созданный элемент проекта, создайте шаблон проекта или шаблон элемента проекта. Дополнительные сведения см. в разделе [Создание шаблонов элементов и проектов для элементов проекта SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Чтобы развернуть элемент проекта, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки, шаблон и другие файлы, которые требуется распространить с элементом проекта. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Определение типов элементов проектов SharePoint, пользовательские](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Способ: добавить свойство типа элемента проекта SharePoint, пользовательские](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Практическое руководство. Добавление пункта контекстного меню в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  