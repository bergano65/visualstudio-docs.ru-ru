---
title: Как добавить пункт контекстного меню в проекты SharePoint | Документация Майкрософт
titleSuffix: ''
description: Добавление пункта контекстного меню в проект SharePoint в Visual Studio. Пункт меню появляется при щелчке правой кнопкой мыши узла проекта в обозреватель решений.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 4244fb83d4792786baeb99693dc0fee04624d37d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882730"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Как добавить пункт контекстного меню в проекты SharePoint
  Пункт контекстного меню можно добавить в любой проект SharePoint. Этот пункт меню появляется, когда пользователь щелкает правой кнопкой мыши узел проекта в **Обозреватель решений**.

 В следующих шагах предполагается, что вы уже создали расширение проекта. Дополнительные сведения см. [в разделе инструкции. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Добавление пункта контекстного меню в проекты SharePoint

1. В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> реализации обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> событие параметра *прожектсервице* .

2. В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> события добавьте новый <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объект в <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> коллекцию или параметра аргументов события.

3. В <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> обработчике событий для нового <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объекта выполните задачи, которые необходимо выполнить, когда пользователь щелкнет нужный пункт контекстного меню.

## <a name="example"></a>Пример
 В следующем примере кода показано, как добавить пункт контекстного меню в узлы проекта SharePoint в **Обозреватель решений**. Когда пользователь щелкает правой кнопкой мыши узел проекта и щелкает пункт меню " **запись сообщения в окно вывода** ", Visual Studio отображает сообщение в окне **вывода** . В этом примере для вывода сообщения используется служба проекта SharePoint. Дополнительные сведения см. [в статье Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуется проект библиотеки классов со ссылками на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Как создать расширение проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Как добавить свойство в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
