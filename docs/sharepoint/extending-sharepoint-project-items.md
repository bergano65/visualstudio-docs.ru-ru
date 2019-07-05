---
title: Расширение элементов проектов SharePoint | Документация Майкрософт
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
ms.openlocfilehash: f60c95418379399196c461e055645ae7c85a473e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967400"
---
# <a name="extend-sharepoint-project-items"></a>Расширение элементов проектов SharePoint
  Создание расширения элемента проекта, если вы хотите добавить функции к типу элемента проекта SharePoint, который уже установлен в Visual Studio. Например, можно создать расширение для встроенной **приемника событий** или **определение списка** элементы проекта в Visual Studio, или можно создать расширение для пользовательского типа элемента проекта. Кроме того, можно создать расширение для всех типов элементов проекта SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Задачи для расширение элементов проектов SharePoint
 Чтобы расширить возможности элемент проекта, создайте сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> интерфейс. Дополнительные сведения см. в разделе [Как Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 При расширении элемента проекта, можно также добавить следующие функциональные возможности на элемент проекта:

- Добавление пункта контекстного меню к элементу проекта. Этот пункт меню отображается при открытии контекстное меню для элемента проекта в **обозревателе решений**. Откройте контекстное меню, щелкнув правой кнопкой мыши элемент проекта или выбрав его, а затем выбрать **Shift**+**F10** ключи. Дополнительные сведения см. в разделе [Как Добавление пункта контекстного меню в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Добавьте пользовательское свойство к элементу проекта. Свойство отображается в **свойства** окно при выборе элемента проекта в **обозревателе решений**. Дополнительные сведения см. в разделе [Как Добавление свойства в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Пошаговое руководство для создания, развертывания и тестирования в расширение элемента проекта см. в разделе [Пошаговое руководство: Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Взаимосвязь между расширениям элемента проекта и экземпляров элементов проекта
 При создании расширения элемента проекта, Visual Studio загружает расширение, когда элемент проекта, сопоставленного типа добавляется в проект SharePoint. Например, при создании расширения для **приемника событий** элементов проекта, Visual Studio загружает расширение, когда пользователь добавляет **приемника событий** элемент проекта в проект. Visual Studio использует один экземпляр расширения для всех экземпляров типа элемента проекта. В предыдущем примере, если пользователь добавит секунды **приемника событий** элемента проекта в проект, один и тот же экземпляр расширения используется для настройки второго элемента проекта.

 Чтобы открыть экземпляр конкретного типа элемента проекта, вы расширяете, обработку одного из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> события *projectItemType* параметра в текущей реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метод. Например, чтобы определить, когда вы расширяемого типа элемента проекта добавляется в проект, обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> событий. Дополнительные сведения см. в разделе [Как Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Идентификаторы для элементов проекта SharePoint
 Каждый элемент проекта SharePoint имеет соответствующий идентификатор строки. Необходимо знать идентификатор для элемента проекта, если вы хотите выполнять следующие задачи:

- Создание расширения элемента проекта. В этом случае необходимо передать идентификатор для элемента проекта, который вы хотите расширить конструктору <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Чтобы создать расширение для всех элементов типов проектов, передайте **\\** * строковое значение.

- Добавьте элемент проекта в проект программным способом. В этом случае необходимо передать идентификатор элемента проекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> метод.

  В следующей таблице перечислены идентификаторы для элементов проекта SharePoint, которые входят в состав Visual Studio.

|Имя элемента проекта|Идентификатор строки|
|-----------------------|-----------------------|
|Модель каталога бизнес-данным|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|
|Тип содержимого|Microsoft.VisualStudio.SharePoint.ContentType|
|Приемник событий|Microsoft.VisualStudio.SharePoint.EventHandler|
|Пустой элемент|Microsoft.VisualStudio.SharePoint.GenericElement|
|Определение списка<br /><br /> Определение списка из типа содержимого|Microsoft.VisualStudio.SharePoint.ListDefinition|
|Экземпляр списка|Microsoft.VisualStudio.SharePoint.ListInstance|
|Module|Microsoft.VisualStudio.SharePoint.Module|
|Последовательный рабочий процесс<br /><br /> Рабочий процесс конечного компьютера|Microsoft.VisualStudio.SharePoint.Workflow|
|Определение веб-сайта|Microsoft.VisualStudio.SharePoint.SiteDefinition|
|Визуальная веб-часть|Microsoft.VisualStudio.SharePoint.VisualWebPart|
|Веб-часть|Microsoft.VisualStudio.SharePoint.WebPart|
|Форма сопоставления рабочего процесса|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|

## <a name="see-also"></a>См. также
- [Практическое руководство. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Практическое руководство. Добавление пункта контекстного меню в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Практическое руководство. Добавление свойства в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Пошаговое руководство: Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
