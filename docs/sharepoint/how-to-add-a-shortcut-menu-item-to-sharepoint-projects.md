---
title: 'Как: Добавление пункта контекстного меню в проекты SharePoint | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0aea2dd600548d76d57d58c8cfc0313c92ccb9f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Практическое руководство. Добавление пункта контекстного меню в проекты SharePoint
  Команды контекстного меню можно добавить в любой проект SharePoint. Пункт меню отображается, когда пользователь щелкает правой кнопкой мыши узел проекта в **обозревателе решений**.  
  
 Следующие шаги предполагают, что вы уже создали расширения проекта. Дополнительные сведения см. в разделе [как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Добавление пункта контекстного меню в проекты SharePoint  
  
1.  В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метод вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> реализацию, дескриптор <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> событие *projectService* параметра.  
  
2.  В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> события, добавьте новый <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объект <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> или <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> коллекцию параметра аргументов события.  
  
3.  В <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> обработчик событий для нового <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объекта, выполнять задачи, которые требуется выполнить при щелчке пункта контекстного меню.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется добавление пункта контекстного меню узел проекта SharePoint в **обозревателе решений**. Когда пользователь щелкает правой кнопкой мыши узел проекта и нажимает кнопку **написать сообщение в окно вывода** пункт меню, Visual Studio отображает сообщение в **вывода** окна. В этом примере используется служба проекта SharePoint для отображения сообщений. Дополнительные сведения см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В этом примере требуется проект библиотеки классов с ссылками на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Практическое руководство. Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  