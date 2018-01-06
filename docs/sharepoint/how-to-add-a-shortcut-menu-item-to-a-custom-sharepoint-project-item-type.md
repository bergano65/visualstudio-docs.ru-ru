---
title: "Как: Добавление пункта контекстного меню для типа элемента проекта SharePoint пользовательских | Документы Microsoft"
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6875b03c86580328f2e29f701b77c07d646ffca1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Практическое руководство. Добавление пункта контекстного меню в пользовательский тип элемента проекта SharePoint
  При определении настраиваемого типа элемента проекта SharePoint, можно добавить команды контекстного меню в элемент проекта. Этот пункт меню отображается при щелчке элемента проекта в **обозревателе решений**.  
  
 Следующие шаги предполагают, что собственный тип элемента проекта SharePoint уже определены. Дополнительные сведения см. в разделе [как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Добавление пункта контекстного меню для пользовательского типа элементов проектов  
  
1.  В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> реализацию, дескриптор <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> событие *projectItemTypeDefinition* параметра.  
  
2.  В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> события, добавьте новый <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объект <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> или <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> коллекцию параметра аргументов события.  
  
3.  В <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> обработчик событий для нового <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объекта, выполнять задачи, которые требуется выполнить при выборе пункта контекстного меню.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется добавление пункта контекстного меню к настраиваемому типу элемента проекта. Когда пользователь открывает контекстное меню в элемент проекта в **обозревателе решений** и выбирает **написать сообщение в окно вывода** пункт меню, Visual Studio отображает сообщение в **выходных данных**  окна.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 В этом примере используется служба проекта SharePoint для записи сообщения для **вывода** окна. Дополнительные сведения см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В этом примере требуется проект библиотеки классов с ссылками на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Развертывание элемента проекта  
 Чтобы включить другие разработчики также могли использовать созданный элемент проекта, создайте шаблон проекта или шаблон элемента проекта. Дополнительные сведения см. в разделе [Создание шаблонов элементов и проектов для элементов проекта SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Чтобы развернуть элемент проекта, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки, шаблон и другие файлы, которые требуется распространить с элементом проекта. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Способ: добавить свойство типа элемента проекта SharePoint, пользовательские](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  