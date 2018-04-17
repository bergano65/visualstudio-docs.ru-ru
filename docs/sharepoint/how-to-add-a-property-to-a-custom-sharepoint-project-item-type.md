---
title: 'Способ: добавить свойство типа элемента проекта SharePoint пользовательских | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2da3ebd75ef8b195b0e4c6117b28a6bc294ac050
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Практическое руководство. Добавление свойства в пользовательский тип элемента проекта SharePoint
  При определении настраиваемого типа элемента проекта SharePoint, можно добавить свойства в элемент проекта. Это свойство отображается в **свойства** окно при выборе элемента проекта в **обозревателе решений**.  
  
 Следующие шаги предполагают, что собственный тип элемента проекта SharePoint уже определены. Дополнительные сведения см. в разделе [как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Чтобы добавить свойство в определении типа элемента проекта  
  
1.  Определите класс с открытым свойством, которое представляет свойство, которое добавляется к настраиваемому типу элемента проекта. Если требуется добавить несколько свойств пользовательского элемента типа проектов можно определить все свойства в том же классе или в различных классах.  
  
2.  В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> реализацию, дескриптор <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событие *projectItemTypeDefinition* параметра.  
  
3.  В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событий, нужно добавить экземпляр пользовательского класса свойств для <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> коллекцию параметра аргументов события.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как добавить свойство с именем **пример свойства** для пользовательского элемента проекта типа.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understanding-the-code"></a>Общие сведения о коде  
 Чтобы убедиться, что тот же экземпляр `CustomProperties` класса используется каждый раз <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> происходит событие, в примере кода сохраняет объект свойств в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство проекта, когда это событие происходит первым. Код получает этот объект, когда происходит данное событие. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство для сохранения данных с элементами проекта в разделе [связывание пользовательских данных с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Сохранение изменений для значения свойства **задать** доступа для `ExampleProperty` сохраняет новое значение для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> , свойство, связанное с объектом. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство для сохранения данных с элементами проекта в разделе [сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Задание поведения пользовательских свойств  
 Можно определить как пользовательское свойство выглядит и работает в **свойства** окна путем применения атрибутов из <xref:System.ComponentModel> пространство имен для определения свойства. Во многих сценариях полезны следующие атрибуты:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Задает имя свойства, которое отображается в **свойства** окна.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Задает строку описания, которое отображается в нижней части **свойства** окно при выборе данного свойства.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Задает значение свойства по умолчанию.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Задает настраиваемое преобразование между строкой, которая отображается в **свойства** окна и значение свойства, не являющегося строкой.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Задает пользовательский редактор для изменения свойства.  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Эти примеры кода требуется проект библиотеки классов со ссылками на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Развертывание элемента проекта  
 Чтобы включить другие разработчики также могли использовать созданный элемент проекта, создайте шаблон проекта или шаблон элемента проекта. Дополнительные сведения см. в разделе [Создание шаблонов элементов и проектов для элементов проекта SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Чтобы развернуть элемент проекта, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки, шаблон и другие файлы, которые требуется распространить с элементом проекта. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Как: Добавление пункта контекстного меню для типа элемента проекта SharePoint, пользовательские](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  