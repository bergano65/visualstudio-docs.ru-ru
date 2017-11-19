---
title: "Расширение проектов SharePoint | Документы Microsoft"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d0bbb086c66bad3ad2beedab2b390244a9e185b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="extending-sharepoint-projects"></a>Расширение проектов SharePoint
  Создание расширения проекта, если вы хотите настроить функции уровня проекта проектов SharePoint. Например можно добавить пользовательские свойства проекта или в ответ на события на уровне проекта, возникающие при разработке решения SharePoint в Visual Studio.  
  
## <a name="creating-project-extensions"></a>Создание проекта расширения  
 Чтобы расширить элемент проекта, создайте сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейса. Дополнительные сведения см. в разделе [как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 При создании расширения проекта, также можно добавить следующие функциональные возможности для проектов SharePoint:  
  
-   Добавление пункта контекстного меню. Элемент меню появляется, когда открывается контекстное меню для узла проекта SharePoint в **обозревателе решений** , щелкнув правой кнопкой мыши узел или выбрав его и нажмите клавиши Shift + F10 ключей. Дополнительные сведения см. в разделе [как: Добавление пункта контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Добавление пользовательского свойства. Это свойство отображается в **свойства** при выборе проекта SharePoint в **обозревателе решений**. Дополнительные сведения см. в разделе [как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Пошаговое руководство для создания, развертывания и тестирования расширения проекта в разделе [Пошаговое руководство: создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understanding-the-relationship-between-project-extensions-and-project-instances"></a>Основные сведения о связи между расширениями проекта и экземплярами проекта  
 При создании расширения проекта это расширение загружается при открытии любого проекта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]включает несколько шаблонов проекта SharePoint, такие как определения списков, типы содержимого и приемников событий. Тем не менее есть только один тип проекта SharePoint. Типы проектов, которые отображаются в **новый проект** диалоговое окно — это только шаблоны, которые объединены один или несколько элементов проекта SharePoint. Поскольку имеется только один тип проекта SharePoint, расширения, созданные для одного проекта применяются ко всем проектам SharePoint. Например, нельзя создать расширение, которое применяется только к **тип содержимого** проекта.  
  
 Для доступа к определенным экземплярам проекта, обработку одного из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> события *projectService* параметр в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метод. Например, чтобы определить, когда проект SharePoint добавляется в решение, обрабатывают <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> событий. Дополнительные сведения см. в разделе [как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>См. также  
 [Как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Как: Добавление пункта контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Пошаговое руководство: Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Определение типов элементов проектов SharePoint, пользовательские](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  