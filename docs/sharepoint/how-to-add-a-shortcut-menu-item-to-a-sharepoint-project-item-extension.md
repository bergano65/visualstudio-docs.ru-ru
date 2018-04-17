---
title: 'Как: Добавление пункта контекстного меню в расширение элемента проекта SharePoint | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b2ac26672e7df8cc01fbca862df5867787e5283c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Практическое руководство. Добавление пункта контекстного меню в расширение элемента проекта SharePoint
  Команды контекстного меню можно добавить в существующий элемент проекта SharePoint с помощью расширения элемента проекта. Этот пункт меню отображается при щелчке элемента проекта в **обозревателе решений**.  
  
 Следующие шаги предполагают, что вы уже создали расширение элемента проекта. Дополнительные сведения см. в разделе [как: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Добавление пункта контекстного меню в расширение элемента проекта  
  
1.  В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метод вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> реализацию, дескриптор <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> событие *изменить* параметра.  
  
2.  В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> события, добавьте новый <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объект <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> или <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> коллекцию параметра аргументов события.  
  
3.  В <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> обработчик событий для нового <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объекта, выполнять задачи, которые требуется выполнить при щелчке пункта контекстного меню.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется добавление пункта контекстного меню в элемент проекта приемника событий. При щелчке правой кнопкой мыши на элемент проекта в **обозревателе решений** и нажимает кнопку **написать сообщение в окно вывода** пункт меню, Visual Studio отображает сообщение в **вывода**окна.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]  
  
 В этом примере используется служба проекта SharePoint для записи сообщения для **вывода** окна. Дополнительные сведения см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В этом примере требуется проект библиотеки классов с ссылками на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Как: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Как: Добавление свойства в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Пошаговое руководство. Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  