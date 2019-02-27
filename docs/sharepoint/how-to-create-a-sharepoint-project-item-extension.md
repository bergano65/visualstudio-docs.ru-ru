---
title: Практическое руководство. Создание расширения элемента проекта SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 42cea2633ceb0cbda1c63b76a4e2b7775e967bc2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597105"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Практическое руководство. Создание расширения элемента проекта SharePoint
  Создание расширения элемента проекта, если вы хотите добавить функциональные возможности для элемента проекта SharePoint, который уже установлен в Visual Studio. Дополнительные сведения см. в разделе [элементы проекта SharePoint, расширить](../sharepoint/extending-sharepoint-project-items.md).

### <a name="to-create-a-project-item-extension"></a>Создание расширения элемента проекта

1.  Создайте проект библиотеки классов.

2.  Добавьте ссылки на следующие сборки:

    -   Microsoft.VisualStudio.SharePoint

    -   System.ComponentModel.Composition

3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.

4.  Добавьте следующие атрибуты к классу:

    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Этот атрибут позволяет Visual Studio для обнаружения и загрузки вашего <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> тип конструктору атрибута.

    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. В расширение элемента проекта этот атрибут определяет элемент проекта, который требуется расширить. Идентификатор элемента проекта, передайте конструктору атрибута. Список идентификаторов элементов проекта, которые входят в состав Visual Studio, см. в разделе [элементы проекта SharePoint, расширить](../sharepoint/extending-sharepoint-project-items.md).

5.  В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метода, *используйте членами* параметра для определения поведения вашего расширения. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> объект, предоставляющий доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> интерфейсов. Для доступа к определенного экземпляра типа элемента проекта, вы расширяете, обработку <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> события, такие как <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.

## <a name="example"></a>Пример
 В следующем примере кода показано, как создать простое расширение для элемента проекта приемника событий. Каждый раз пользователь добавляет элемент проекта приемника событий в проект SharePoint, это расширение записывает сообщение **вывода** окна и **список ошибок** окна.

 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]

 В этом примере используется служба проекта SharePoint для записи сообщения в **вывода** окна и **список ошибок** окна. Дополнительные сведения см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере требуются ссылки на следующие сборки:

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Пошаговое руководство: Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
