---
title: "How to: Add a Property to a Custom SharePoint Project Item Type"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 47e940f6-1779-4530-aea6-c43a370c544f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Add a Property to a Custom SharePoint Project Item Type
  При определении настраиваемого типа элемента проекта SharePoint ему можно добавить свойство.  Свойство отображается в окне **Свойства** при выборе элемента проекта в **обозревателе решений**.  
  
 В описании следующих действий предполагается, что читатель уже определил собственный тип элемента проекта SharePoint.  Дополнительные сведения см. в разделе [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### Добавление свойства в определении типа элемента проекта  
  
1.  Определение класса с общедоступным свойством, представляющим свойство, добавляемое к настраиваемому типу элемента проекта.  Для добавления нескольких свойств к настраиваемому типу элемента проекта можно определить все свойства в одном классе или задать их в разных классах.  
  
2.  В методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> обработайте событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> параметра *projectItemTypeDefinition*.  
  
3.  В обработчике событий для события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> добавьте экземпляр пользовательского класса свойств в коллекцию <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> параметра аргументов события.  
  
## Пример  
 В следующем примере кода демонстрируется добавление свойства с именем **Пример свойства** к настраиваемому типу элемента проекта.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#11)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#11)]  
  
### Общие сведения о коде  
 Чтобы обеспечить использование одного и того же экземпляра класса `CustomProperties` всякий раз, когда происходит событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>, пример кода сохраняет объект свойств в свойстве <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> элемента проекта, когда это событие происходит впервые.  Когда событие происходит снова, код извлекает этот объект.  Дополнительные сведения об использовании свойства <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> для сохранения данных вместе с элементами проекта см. в разделе [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Для сохранения изменений в значении свойства метод доступа **set** для свойства `ExampleProperty` сохраняет новое значение в свойстве <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>, с которым это свойство связано.  Дополнительные сведения об использовании свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> для сохранения данных вместе с элементами проекта см. в разделе [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Определение поведения настраиваемых свойств  
 Отображение и поведение настраиваемого свойства можно определить в окне **Свойства**, применив к определению этого свойства атрибуты из пространства имен <xref:System.ComponentModel>.  Во многих сценариях удобно использовать перечисленные ниже атрибуты.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> — задает имя свойства, которое отображается в окне **Свойства**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> — задает строку описания, которая отображается в нижней части окна **Свойства** при выборе данного свойства.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute> — задает значение свойства по умолчанию.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute> — задает настраиваемое преобразование между строкой, отображаемой в окне **Свойства**, и нестроковым значением свойства.  
  
-   <xref:System.ComponentModel.EditorAttribute> — задает пользовательский редактор, который необходимо использовать для изменения свойства.  
  
## Компиляция кода  
 Для таких примеров кода требуется проект библиотеки классов со ссылками на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание элемента проекта  
 Чтобы другие разработчики также могли использовать созданный элемент проекта, создайте шаблон проекта или шаблон элемента проекта.  Дополнительные сведения см. в разделе [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Чтобы развернуть элемент проекта, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки, шаблона и всех остальных файлов, которые предполагается распространять с элементом проекта.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  