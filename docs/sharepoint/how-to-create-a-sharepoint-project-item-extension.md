---
title: Как создать расширение элемента проекта SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 345bfa49da4bf5d5b73fe1d3f209675fe2814de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015344"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Как создать расширение элемента проекта SharePoint
  Расширение элемента проекта создается, если требуется добавить функциональные возможности в элемент проекта SharePoint, уже установленный в Visual Studio. Дополнительные сведения см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).

### <a name="to-create-a-project-item-extension"></a>Создание расширения элемента проекта

1. Создайте проект библиотеки классов.

2. Добавьте ссылки на следующие сборки:

    - Microsoft. VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.

4. Добавьте в класс следующие атрибуты:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Этот атрибут позволяет Visual Studio обнаруживать и загружать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> реализацию. Передайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> тип в конструктор атрибута.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. В расширении элемента проекта этот атрибут определяет элемент проекта, который требуется расширить. Передайте идентификатор элемента проекта конструктору атрибута. Список идентификаторов элементов проекта, которые входят в состав Visual Studio, см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).

5. В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метода используйте члены параметра *прожектитемтипе* , чтобы определить поведение вашего расширения. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> объектом, предоставляющим доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> интерфейсах и. Для доступа к определенному экземпляру типа элемента проекта, который вы расширяете, обрабатывайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> события, такие как <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Пример
 В следующем примере кода показано, как создать простое расширение для элемента проекта приемника событий. Каждый раз, когда пользователь добавляет элемент проекта приемника событий в проект SharePoint, это расширение записывает сообщение в окно **вывода** и **Список ошибок** окно.

 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]

 В этом примере используется служба проекта SharePoint для записи сообщения в окно **вывода** и **Список ошибок** окно. Дополнительные сведения см. [в статье Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Пошаговое руководство. расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
