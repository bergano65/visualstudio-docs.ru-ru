---
title: "How to: Add a Property to SharePoint Projects"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Property to SharePoint Projects
  С помощью расширения проекта можно добавить свойство в любой проект SharePoint.  Свойство отображается в окне **Свойства** при выборе проекта в **обозревателе решений**.  
  
 В описании следующих действий предполагается, что расширение проекта уже создано.  Дополнительные сведения см. в разделе [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### Добавление свойства в проект SharePoint  
  
1.  Определите класс с общедоступным свойством, представляющим свойство, добавляемое в проекты SharePoint.  Если требуется добавить несколько свойств в проект, можно определить все свойства в одном классе или задать их в разных классах.  
  
2.  В методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> обработайте событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> параметра *projectService*.  
  
3.  В обработчике событий для события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> добавьте экземпляр класса свойств в коллекцию <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> параметра аргументов события.  
  
## Пример  
 В следующем примере кода демонстрируется добавление двух свойств в проекты SharePoint.  Для одного из них данные сохраняются в файле пользовательских параметров проекта \(с расширением CSPROJ.USER или VBPROJ.USER\).  Для другого свойства данные сохраняются в файле проекта \(с расширением CSPROJ или VBPROJ\).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#1)]
 [!code-vb[SpExt_SPCustomPrjProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#1)]  
  
### Общие сведения о коде  
 Чтобы обеспечить использование одного и того же экземпляра класса `CustomProjectProperties` при каждом возникновении события <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>, пример кода добавляет объект свойств в свойство <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> проекта, когда это событие происходит впервые.  Когда событие происходит снова, код извлекает этот объект.  Дополнительные сведения об использовании свойства <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> для связывания данных с проектами см. в разделе [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Чтобы сохранить изменения значений свойств, методы доступа **set** для этих свойств используют следующие API:  
  
-   Свойство `CustomUserFileProperty` использует свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> для сохранения своего значения в файл пользовательских параметров проекта.  
  
-   Свойство `CustomProjectFileProperty` использует метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> для сохранения своего значения в файл проекта.  
  
 Дополнительные сведения о сохранении данных в этих файлах см. в разделе [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Определение поведения настраиваемых свойств  
 Отображение и поведение настраиваемого свойства можно определить в окне **Свойства**, применив к определению этого свойства атрибуты из пространства имен <xref:System.ComponentModel>.  Во многих сценариях удобно использовать перечисленные ниже атрибуты.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> — задает имя свойства, которое отображается в окне **Свойства**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> — задает строку описания, которая отображается в нижней части окна **Свойства** при выборе данного свойства.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute> — задает значение свойства по умолчанию.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute> — задает настраиваемое преобразование между строкой, отображаемой в окне **Свойства**, и нестроковым значением свойства.  
  
-   <xref:System.ComponentModel.EditorAttribute> — задает пользовательский редактор, который необходимо использовать для изменения свойства.  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## Развертывание расширения  
 Чтобы развернуть расширение, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  