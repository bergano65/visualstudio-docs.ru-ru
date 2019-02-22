---
title: Практическое руководство. Определить тип элемента проекта SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 589e6f5fd102cdd2a69bc63bf623142c14337678
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639236"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Практическое руководство. Определить тип элемента проекта SharePoint
  Определите тип элемента проекта для создания пользовательского элемента проекта SharePoint. Дополнительные сведения см. в разделе [определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).

### <a name="to-define-a-project-item-type"></a>Для определения типа элемента проекта

1.  Создайте проект библиотеки классов.

2.  Добавьте ссылки на следующие сборки:

    -   Microsoft.VisualStudio.SharePoint

    -   System.ComponentModel.Composition

3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.

4.  Добавьте следующие атрибуты к классу:

    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Этот атрибут позволяет Visual Studio для обнаружения и загрузки вашего <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> тип конструктору атрибута.

    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. В определении типа элемента проекта этот атрибут задает идентификатор строки для нового элемента проекта. Мы рекомендуем использовать формат *название компании*. *Имя компонента* для того, чтобы гарантировать, что все элементы проекта иметь уникальное имя.

    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Этот атрибут задает значок, отображаемый для этого элемента проекта в **обозревателе решений**. Этот атрибут является необязательным; Если не применить его к классу, Visual Studio отображает значок по умолчанию для элемента проекта. Если присвоить этому атрибуту, передайте полное имя значка или точечного рисунка, внедренного в сборку.

5.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метода, используйте членами *projectItemTypeDefinition* параметра для определения поведения типа элемента проекта. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> объект, предоставляющий доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> интерфейсов. Чтобы получить доступ к определенному экземпляру типа элемента проекта, обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> события, такие как <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.

## <a name="example"></a>Пример
 В следующем примере кода демонстрируется определение простого типа проектного элемента. Этот тип элемента проекта записывает сообщение в **вывода** окна и **список ошибок** окно, когда пользователь добавляет элемент проекта этого типа в проект.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]

 В этом примере используется служба проекта SharePoint для записи сообщения в **вывода** окна и **список ошибок** окна. Дополнительные сведения см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере требуются ссылки на следующие сборки:

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Развернуть элемент проекта
 Чтобы другие разработчики могли использовать созданный элемент проекта, создайте шаблон проекта или шаблона элемента проекта. Дополнительные сведения см. в разделе [создание элементов, шаблоны и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Чтобы развернуть элемент проекта, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки, шаблон и другие файлы, которые вы хотите распространять вместе с элементом проекта. Дополнительные сведения см. в разделе [средства развертывания расширений для SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Создание шаблонов элементов и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Практическое руководство. Добавление свойства в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Практическое руководство. Добавление пункта контекстного меню в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
