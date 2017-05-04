---
title: "Extending SharePoint Project Items | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Extending SharePoint Project Items
  Расширение элемента создается в случаях, когда требуется добавить функции к уже установленному в Visual Studio типу элемента проекта SharePoint.  Например, можно создать расширение для встроенных элементов проектов **Приемник событий** или **Определение списка** в Visual Studio либо для пользовательского типа элементов проектов.  Также возможно создание расширения всех типов элементов проектов SharePoint.  
  
## Задачи по расширению элементов проектов SharePoint  
 Чтобы расширить элемент проекта, необходимо построить сборку расширения Visual Studio, которая реализует интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Дополнительные сведения см. в разделе [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 При расширении элемента проекта к нему можно добавить следующие функциональные возможности.  
  
-   Добавление пункта контекстного меню в элемент проекта.  Пункт меню отображается при открытии контекстное меню для элемента проекта в **Обозреватель решений**.  Открыть контекстное меню, щелкните правой кнопкой мыши элемент проекта или путем выбора его и затем выбрать ключи миграцию \+ F10.  Дополнительные сведения см. в разделе [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Добавление пользовательского свойства к элементу проекта.  Свойство отображается в окне **Свойства** при выборе элемента проекта в **Обозреватель решений**.  Дополнительные сведения см. в разделе [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Пошаговое руководство по созданию, развертыванию и тестированию расширения элемента проекта см. в разделе [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## Общие сведения о связи между расширениями элементов проектов и экземплярами элементов проектов  
 При создании расширения элементов проектов Visual Studio загружает расширение в то время, как элементы проектов связанного с ним типа добавляются к проекту SharePoint.  Например, при создании расширения элемента проекта **Приемник событий** Visual Studio загружает расширение в то время, как пользователь добавляет элемент проекта **Приемник событий** к проекту.  Visual Studio использует один и тот же экземпляр расширения для всех экземпляров связанного типа элементов проектов.  В предыдущем примере при добавлении пользователем второго элемента проекта **Приемник событий** к проекту для настройки второго элемента проекта используется один и тот же экземпляр расширения.  
  
 Для доступа к определенным экземплярам расширяемых типов элементов проектов выполните обработку одного из событий <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> параметра *projectItemType* реализации метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>.  Например, чтобы определить время добавления элемента проекта расширяемого типа к проекту, выполните обработку события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>.  Дополнительные сведения см. в разделе [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## Идентификаторы элементов проектов SharePoint  
 У каждого элемента проекта SharePoint имеется соответствующий строковый идентификатор.  Идентификатор элемента проекта нужно знать для выполнения следующих задач:  
  
-   создание расширения элемента проекта.  В этом случае необходимо передать идентификатор элемента проекта, который требуется расширить, конструктору <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Для создания расширения всех типов элементов проектов следует передать значение строки **\***.  
  
-   добавление элемента проекта в проект программным образом.  В этом случае необходимо передать идентификатор элемента проекта методу <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>.  
  
 В следующей таблице перечислены идентификаторы элементов проектов SharePoint, которые входят в состав Visual Studio.  
  
|Имя элемента проекта|Строковый идентификатор|  
|--------------------------|-----------------------------|  
|Модель каталога бизнес\-данных|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Тип содержимого|Microsoft.VisualStudio.SharePoint.ContentType|  
|Приемник событий|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Пустой элемент|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Определение списка<br /><br /> Определение списка из типа содержимого|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Экземпляр списка|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Модуль|Microsoft.VisualStudio.SharePoint.Module|  
|Последовательный рабочий процесс<br /><br /> Рабочий процесс конечного компьютера|Microsoft.VisualStudio.SharePoint.Workflow|  
|Определение сайта|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Визуальная веб\-часть|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Веб\-часть|Microsoft.VisualStudio.SharePoint.WebPart|  
|Форма связывания рабочих процессов|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## См. также  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  