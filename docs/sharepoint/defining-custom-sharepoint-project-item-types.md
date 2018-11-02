---
title: Определение типов элементов проектов SharePoint пользовательских | Документация Майкрософт
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
ms.openlocfilehash: f32f429186aa0c4a657503ca9744bf570d624f25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869513"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Определение пользовательских типов элементов проектов SharePoint
  Определите новый тип элемента проекта SharePoint, если вы хотите создать новый тип элемента проекта SharePoint. Например Visual Studio не включает элементы проекта SharePoint для добавления полей или настраиваемые действия на сайте SharePoint. Можно определить собственные типы элементов проекта SharePoint для создания поля, настраиваемые действия и других типов компонентов SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Задачи по определению типов элементов проектов SharePoint
 Для определения пользовательского типа элемента проекта, построить сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейс. Дополнительные сведения см. в разделе [как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 При определении пользовательского типа элемента проекта, можно также добавить следующие функциональные возможности на элемент проекта:  
  
- Добавление пункта контекстного меню к элементу проекта. Этот пункт меню отображается при открытии контекстное меню для элемента проекта в **обозревателе решений** щелкните правой кнопкой мыши элемент проекта или выбрав его, а затем выбрать **Shift** +  **F10** ключи. Дополнительные сведения см. в разделе [как: Добавление пункта контекстного меню в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
- Добавьте пользовательское свойство к элементу проекта. Свойство отображается в **свойства** окно при выборе элемента проекта в **обозревателе решений**. Дополнительные сведения см. в разделе [как: Добавление свойства пользовательского типа элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
  Чтобы другие разработчики могли использовать созданный элемент проекта в Visual Studio, создайте SPDATA-файл и создать шаблон элемента или шаблон проекта, который связан с элементом проекта. Дополнительные сведения см. в разделе [создание элементов, шаблоны и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Взаимосвязь между типов элементов проектов и экземплярами элементов проектов
 При определении типа элемента проекта SharePoint, Visual Studio загружает расширение, когда элемент проекта, сопоставленного типа добавляется в проект SharePoint. Например, если вы определите новый **настраиваемое действие** типа элемента проекта, Visual Studio загружает расширение, когда пользователь добавляет **настраиваемое действие** элемент проекта в проект. Visual Studio использует один экземпляр расширения для всех экземпляров типа элемента проекта. В предыдущем примере, если пользователь добавит секунды **настраиваемое действие** элемента проекта в проект, один и тот же экземпляр расширения используется для настройки второго элемента проекта.  
  
 Чтобы получить доступ к определенному экземпляру типа элемента проекта, обработку одного из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> события *projectItemTypeDefinition* параметра в текущей реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод. Например, чтобы определить, когда элемент пользовательского типа добавляется в проект, обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> событий. Дополнительные сведения см. в разделе [как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>См. также
 [Как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Практическое: Добавление свойства пользовательского типа элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Практическое: Добавление пункта контекстного меню в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Создание шаблонов элементов и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
