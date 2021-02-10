---
title: Определение пользовательских типов элементов проектов SharePoint | Документация Майкрософт
description: Определите тип настраиваемого элемента проекта SharePoint, если нужно создать новый тип элемента проекта SharePoint.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 00ee9f41695078d8bea5daacf1c0ccfd392a64cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948873"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Определение пользовательских типов элементов проектов SharePoint
  Определите новый тип элемента проекта SharePoint, если нужно создать новый вид элемента проекта SharePoint. Например, Visual Studio не включает элементы проектов SharePoint для добавления полей или настраиваемых действий на сайт SharePoint. Можно определить собственные типы элементов проектов SharePoint для создания полей, настраиваемых действий или других типов компонентов SharePoint.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Задачи для определения типов элементов проектов SharePoint
 Чтобы определить пользовательский тип элемента проекта, создайте сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейс. Дополнительные сведения см. [в разделе инструкции. определение типа элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 При определении пользовательского типа элемента проекта можно также добавить в элемент проекта следующие функциональные возможности:

- Добавление пункта контекстного меню в элемент проекта. Этот пункт меню появляется при открытии контекстного меню элемента проекта в **Обозреватель решений** , если щелкнуть правой кнопкой мыши элемент проекта или выбрать его, а затем нажать клавиши **SHIFT** + **F10** . Дополнительные сведения см. в разделе [инструкции. Добавление пункта контекстного меню в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Добавьте пользовательское свойство в элемент проекта. Свойство отображается в окне **Свойства** при выборе элемента проекта в **Обозреватель решений**. Дополнительные сведения см. [в разделе инструкции. Добавление свойства в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Чтобы позволить другим разработчикам использовать элемент проекта в Visual Studio, создайте файл. DataTemplate и создайте шаблон элемента или проекта, связанный с элементом проекта. Дополнительные сведения см. в разделе [Создание шаблонов элементов и шаблонов проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Общие сведения о связи между типами элементов проектов и экземплярами элементов проектов
 При определении типа элемента проекта SharePoint Visual Studio загружает расширение при добавлении элемента проекта связанного типа в проект SharePoint. Например, при определении нового типа элемента проекта **настраиваемого действия** Visual Studio загружает расширение, когда пользователь добавляет элемент проекта **настраиваемого действия** в проект. Visual Studio использует один и тот же экземпляр расширения для всех экземпляров связанного типа элемента проекта. В предыдущем примере, если пользователь добавляет в проект второй элемент проекта **настраиваемого действия** , то для настройки второго элемента проекта используется тот же экземпляр расширения.

 Чтобы получить доступ к определенному экземпляру типа элемента проекта, обработайте одно из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> событий параметра *прожектитемтипедефинитион* в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метода. Например, чтобы определить, когда элемент проекта настраиваемого типа добавляется в проект, обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> событие. Дополнительные сведения см. [в разделе инструкции. определение типа элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>См. также раздел
- [Как определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Как добавить свойство в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Как добавить пункт контекстного меню в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
