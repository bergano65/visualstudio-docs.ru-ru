---
title: "How to: Add a Property to a SharePoint Project Item Extension | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# How to: Add a Property to a SharePoint Project Item Extension
  Расширение элемента проекта можно использовать для добавления свойства в любой элемент проекта SharePoint, который уже установлен в Visual Studio.  Свойство отображается в окне **Свойства** при выборе элемента проекта в **обозревателе решений**.  
  
 В описании следующих действий предполагается, что расширение элемента проекта уже создано.  Дополнительные сведения см. в разделе [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### Добавление свойства в расширение элемента проекта  
  
1.  Определите класс с общедоступным свойством, представляющим свойство, добавляемое к типу проектного элемента.  Для добавления нескольких свойств к типу элемента проекта можно определить все свойства в одном классе или задать их в разных классах.  
  
2.  В методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> обработайте событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> параметра *projectItemType*.  
  
3.  В обработчике событий для события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> добавьте экземпляр класса свойств в коллекцию <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> параметра аргументов события.  
  
## Пример  
 В следующем примере кода демонстрируется добавление свойства с именем **Пример свойства** к элементу проекта "Приемник события".  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionproperty.vb#8)]  
  
### Общие сведения о коде  
 Чтобы обеспечить использование одного и того же экземпляра класса `CustomProperties` при каждом возникновении события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>, пример кода добавляет объект свойств в свойство <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> элемента проекта, когда это событие происходит впервые.  Когда событие происходит снова, код извлекает этот объект.  Дополнительные сведения об использовании свойства <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> для связывания данных с элементами проекта см. в разделе [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Для сохранения изменений в значении свойства метод доступа **set** для свойства `ExampleProperty` сохраняет новое значение в свойстве <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>, с которым это свойство связано.  Дополнительные сведения об использовании свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> для сохранения данных вместе с элементами проекта см. в разделе [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Определение поведения настраиваемых свойств  
 Отображение и поведение настраиваемого свойства можно определить в окне **Свойства**, применив к определению этого свойства атрибуты из пространства имен <xref:System.ComponentModel>.  Во многих сценариях удобно использовать перечисленные ниже атрибуты.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> — задает имя свойства, которое отображается в окне **Свойства**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> — задает строку описания, которая отображается в нижней части окна **Свойства** при выборе данного свойства.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute> — задает значение свойства по умолчанию.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute> — задает настраиваемое преобразование между строкой, отображаемой в окне **Свойства**, и нестроковым значением свойства.  
  
-   <xref:System.ComponentModel.EditorAttribute> — задает пользовательский редактор, который необходимо использовать для изменения свойства.  
  
## Компиляция кода  
 Для таких примеров требуется проект библиотеки классов со ссылками на следующие сборки.  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Развертывание расширения  
 Чтобы развернуть расширение, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  