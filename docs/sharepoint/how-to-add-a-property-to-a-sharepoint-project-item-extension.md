---
title: 'Как: Добавление свойства в расширение элемента проекта SharePoint | Документы Microsoft'
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
ms.openlocfilehash: 50cbb0eb3a9c0c24abaa3734b7fa9cbd01e839b7
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766731"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Как: Добавление свойства в расширение элемента проекта SharePoint
  Расширение элемента проекта можно использовать для добавления свойства в любой элемент проекта SharePoint, который уже установлен в Visual Studio. Это свойство отображается в **свойства** окно при выборе элемента проекта в **обозревателе решений**.  
  
 Следующие шаги предполагают, что вы уже создали расширение элемента проекта. Дополнительные сведения см. в разделе [как: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>Добавление свойства в расширение элемента проекта  
  
1.  Определите класс с открытым свойством, которое представляет свойство, которое добавляется к типу элемента проекта. Если требуется добавить несколько свойств для типа элемента проекта, можно определить все свойства в том же классе или в различных классах.  
  
2.  В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метод вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> реализацию, дескриптор <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событие *изменить* параметра.  
  
3.  В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событий, добавьте экземпляр класса свойств <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> коллекцию параметра аргументов события.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как добавить свойство с именем **пример свойства** в элемент проекта приемника событий.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understanding-the-code"></a>Общие сведения о коде  
 Чтобы убедиться, что тот же экземпляр `CustomProperties` класса используется каждый раз <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> происходит событие, пример кода добавляет объект свойств в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство проекта, когда это событие происходит первым. Код получает этот объект, когда происходит данное событие. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство для связывания данных с элементами проекта в разделе [связывание пользовательских данных с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Сохранение изменений для значения свойства **задать** доступа для `ExampleProperty` сохраняет новое значение для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> , свойство, связанное с объектом. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство для сохранения данных с элементами проекта в разделе [сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Задание поведения пользовательских свойств  
 Можно определить как пользовательское свойство выглядит и работает в **свойства** окна путем применения атрибутов из <xref:System.ComponentModel> пространство имен для определения свойства. Во многих сценариях полезны следующие атрибуты:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Задает имя свойства, которое отображается в **свойства** окна.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Задает строку описания, которое отображается в нижней части **свойства** окно при выборе данного свойства.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Задает значение свойства по умолчанию.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Задает настраиваемое преобразование между строкой, которая отображается в **свойства** окна и значение свойства, не являющегося строкой.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Задает пользовательский редактор для изменения свойства.  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этих примеров требуются проект библиотеки классов с ссылками на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также
 [Как: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Как: Добавление пункта контекстного меню в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Пошаговое руководство. Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  
