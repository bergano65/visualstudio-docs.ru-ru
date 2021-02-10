---
title: Расширение проектов SharePoint | Документация Майкрософт
description: Узнайте, как создать расширение проекта, если необходимо настроить функции уровня проекта для проектов SharePoint.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8efeb704bb247e653af0ee062efcc71ad390c5ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948665"
---
# <a name="extend-sharepoint-projects"></a>Расширение проектов SharePoint
  Создайте расширение проекта, если необходимо настроить функции уровня проекта для проектов SharePoint. Например, можно добавить настраиваемые свойства проекта или реагировать на события уровня проекта, возникающие при разработке пользователем решения SharePoint в Visual Studio.

## <a name="create-project-extensions"></a>Создание расширений проекта
 Чтобы расширить элемент проекта, создайте сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейс. Дополнительные сведения см. [в разделе инструкции. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 При создании расширения проекта можно также добавить следующие функциональные возможности в проекты SharePoint:

- Добавление пункта контекстного меню. Пункт меню отображается при открытии контекстного меню узла проекта SharePoint в **Обозреватель решений** щелчком правой кнопкой мыши узла или выбором его, а затем нажатием клавиш **SHIFT** + **F10** . Дополнительные сведения см. [в разделе инструкции. Добавление пункта контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Добавьте пользовательское свойство. Свойство отображается в окне **Свойства** при выборе проекта SharePoint в **Обозреватель решений**. Дополнительные сведения см. [в разделе инструкции. Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Пошаговое руководство, в котором показано, как создать, развернуть и проверить расширение проекта, см. в разделе [Пошаговое руководство. Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Общие сведения о связи между расширениями проекта и экземплярами проекта
 При создании расширения проекта это расширение загружается при открытии любого типа проекта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] содержит несколько шаблонов проектов SharePoint, таких как определения списков, типы содержимого и приемники событий. Однако существует только один тип проекта SharePoint. Типы проектов, отображаемые в диалоговом окне **Новый проект** , — это только шаблоны, объединяющие один или несколько элементов проектов SharePoint. Поскольку существует только один тип проекта SharePoint, расширения, созданные для одного проекта, применяются ко всем проектам SharePoint. Например, нельзя создать расширение, которое применяется только к проекту **типа содержимого** .

 Чтобы получить доступ к определенному экземпляру проекта, обработайте одно из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> событий параметра *прожектсервице* в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метода. Например, чтобы определить, когда проект SharePoint добавляется в решение, обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> событие. Дополнительные сведения см. [в разделе инструкции. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>См. также раздел
- [Как создать расширение проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Как добавить пункт контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Как добавить свойство в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Пошаговое руководство. Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
