---
title: Определение типов элементов проектов SharePoint пользовательских | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d9b752aa8162f52746b4487b863557af6dd37fd9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765584"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Определение пользовательских типов элементов проектов SharePoint
  Определите новый тип элемента проекта SharePoint, если вы хотите создать новый тип элемента проекта SharePoint. Например Visual Studio не включает элементы проекта SharePoint для добавления полей или настраиваемых действий на сайте SharePoint. Можно определить собственные типы элементов проекта SharePoint для создания полей, настраиваемые действия и другие компоненты SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Задачи по определению типов элементов проектов SharePoint
 Чтобы определить тип элемента пользовательского проекта, построить сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейса. Дополнительные сведения см. в разделе [как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 При определении пользовательского типа элементов проектов также можно добавить следующие функциональные возможности для элемента проекта:  
  
-   Добавление пункта контекстного меню в элемент проекта. Элемент меню появляется, когда открывается контекстное меню для элемента проекта в **обозревателе решений** щелкните правой кнопкой мыши элемент проекта или выбрав его и затем выбрав **Shift** +  **F10** ключей. Дополнительные сведения см. в разделе [как: Добавление пункта контекстного меню в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Добавление пользовательского свойства в элемент проекта. Это свойство отображается в **свойства** при выборе элемента проекта в **обозревателе решений**. Дополнительные сведения см. в разделе [как: добавить свойство в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Чтобы включить другие разработчики могли использовать элемент проекта в Visual Studio, создайте SPDATA-файл и создать шаблон элемента или шаблон проекта, который связан с элементом проекта. Дополнительные сведения см. в разделе [Создание шаблонов элементов и проектов для элементов проекта SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Взаимосвязь между типами элементов проектов и экземплярами элементов проектов
 При определении типа элемента проекта SharePoint, Visual Studio загружает расширения элемента проекта связанный тип для добавления в проект SharePoint. Например, если определить новый **пользовательское действие** тип проекта, Visual Studio загружает расширение, когда пользователь добавляет **пользовательское действие** элемента проекта в проект. Visual Studio использует один и тот же экземпляр расширения для всех экземпляров типа элемента, соответствующего проекта. В предыдущем примере, если пользователь добавляет второй **пользовательское действие** элемента проекта в проект, для настройки второго элемента проекта используется один и тот же экземпляр расширения.  
  
 Для доступа к определенному экземпляру типа элемента проекта, обработку одного из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> события *projectItemTypeDefinition* параметр в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод. Например, чтобы определить, при добавлении элемента проекта настраиваемого типа в проект, обрабатывают <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> событий. Дополнительные сведения см. в разделе [как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>См. также
 [Как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Способ: добавить свойство типа элемента проекта SharePoint, пользовательские](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Как: Добавление пункта контекстного меню для типа элемента проекта SharePoint, пользовательские](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
