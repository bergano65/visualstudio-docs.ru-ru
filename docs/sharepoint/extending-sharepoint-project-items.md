---
title: "Расширение элементов проектов SharePoint | Документы Microsoft"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ffbacd5748ae2a5284ed628dce974b20e25bcab3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="extending-sharepoint-project-items"></a>Расширение элементов проектов SharePoint
  Создание расширения элемента проекта, если вы хотите добавить функциональные возможности для типа элемента проекта SharePoint, который уже установлен в Visual Studio. Например, можно создать расширение для встроенной **приемника событий** или **определение списка** элементы проекта в Visual Studio, или можно создать расширение для пользовательского типа элементов проектов. Кроме того, можно создать расширение для всех типов элементов проектов SharePoint.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Задачи по расширению элементов проектов SharePoint  
 Чтобы расширить элемент проекта, создайте сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> интерфейса. Дополнительные сведения см. в разделе [как: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 При расширении элемента проекта, также можно добавить следующие функциональные возможности для элемента проекта:  
  
-   Добавление пункта контекстного меню в элемент проекта. Элемент меню появляется, когда открывается контекстное меню для элемента проекта в **обозревателе решений**. Откройте контекстное меню, щелкнув правой кнопкой мыши элемент проекта или выбрав его, затем нажав клавиши Shift + F10 ключей. Дополнительные сведения см. в разделе [как: Добавление пункта контекстного меню в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Добавление пользовательского свойства в элемент проекта. Это свойство отображается в **свойства** при выборе элемента проекта в **обозревателе решений**. Дополнительные сведения см. в разделе [как: Добавление свойства в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Пошаговое руководство для создания, развертывания и тестирования расширения элемента проекта в разделе [Пошаговое руководство: расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understanding-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Основные сведения о связи между расширениями элементов проектов и экземплярами элементов проектов  
 При создании расширения элемента проекта Visual Studio загружает расширения элемента проекта связанный тип для добавления в проект SharePoint. Например, при создании расширения для **приемника событий** элементов проекта, Visual Studio загружает расширение, когда пользователь добавляет **приемника событий** элемента проекта в проект. Visual Studio использует один и тот же экземпляр расширения для всех экземпляров типа элемента, соответствующего проекта. В предыдущем примере, если пользователь добавляет второй **приемника событий** элемента проекта в проект, для настройки второго элемента проекта используется один и тот же экземпляр расширения.  
  
 Чтобы открыть экземпляр типа элемента проекта, расширении, обработку одного из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> события *изменить* параметр в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метод. Например, чтобы определить, при добавлении в проект элемент проекта расширяемых типов, обработку <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> событий. Дополнительные сведения см. в разделе [как: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Идентификаторы для элементов проектов SharePoint  
 Каждый элемент проекта SharePoint имеет соответствующий идентификатор строки. Необходимо знать идентификатор для элемента проекта, если вы хотите выполнять следующие задачи:  
  
-   Создание расширения элемента проекта. В этом случае необходимо передать идентификатор элемента проекта, который требуется расширить в конструктор <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Чтобы создать расширение для всех элементов типов проектов, необходимо передать  **\***  строковое значение.  
  
-   Добавьте элемент проекта в проект программным способом. В этом случае необходимо передать идентификатор для элемента проекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> метод.  
  
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
 [Как: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Как: Добавление пункта контекстного меню в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Как: Добавление свойства в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Пошаговое руководство: Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  