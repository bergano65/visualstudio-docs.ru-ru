---
title: Расширение проектов SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6bc92d65ed179c7f2cb2f569a7d254a025887845
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635609"
---
# <a name="extend-sharepoint-projects"></a>Расширение проектов SharePoint
  Создание расширения проекта, если вы хотите настроить функции уровня проекта проектов SharePoint. Например можно добавить пользовательские свойства проекта или реагировать на события уровня проекта, возникающих при разработке решения SharePoint в Visual Studio.

## <a name="create-project-extensions"></a>Создание проекта расширения
 Чтобы расширить возможности элемент проекта, создайте сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейс. Дополнительные сведения см. в разделе [Как Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 При создании расширения проекта, в проекты SharePoint можно также добавить следующие функциональные возможности:

- Добавление пункта контекстного меню. Этот пункт меню отображается при открытии контекстное меню для узла проекта SharePoint в **обозревателе решений** , щелкнув правой кнопкой мыши узел или выбрав его, а затем выберите **Shift** +  **F10** ключи. Дополнительные сведения см. в разделе [Как Добавление пункта контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Добавление пользовательского свойства. Свойство отображается в **свойства** окно при выборе проекта SharePoint в **обозревателе решений**. Дополнительные сведения см. в разделе [Как Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Пошаговое руководство для создания, развертывания и тестирования в расширение проекта см. в разделе [Пошаговое руководство: Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Взаимосвязь между расширениями проекта и экземплярами проекта
 При создании расширения проекта, расширение загружается при открытии любого проекта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] включает несколько шаблонов проектов SharePoint, такие как определения списков, типы содержимого и приемников событий. Тем не менее есть только один тип проекта SharePoint. Типы проектов, которые отображаются в **новый проект** диалоговое окно — это только шаблоны, которые объединены один или несколько элементов проекта SharePoint. Поскольку имеется только один тип проекта SharePoint, расширения, созданные для одного проекта применяются ко всем проектам SharePoint. Например, нельзя создать расширение, которое применяется только к **тип содержимого** проекта.

 Для доступа к экземпляру конкретного проекта, обработайте одно из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> события *projectService* параметра в текущей реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метод. Например, чтобы определить, когда проект SharePoint добавляется в решение, обрабатывать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> событий. Дополнительные сведения см. в разделе [Как Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Практическое руководство. Добавление пункта контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Практическое руководство. Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Пошаговое руководство: Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
