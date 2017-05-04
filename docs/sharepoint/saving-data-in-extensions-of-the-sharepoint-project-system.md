---
title: "Saving Data in Extensions of the SharePoint Project System | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint project items, saving string data"
  - "project items [SharePoint development in Visual Studio], saving string data"
  - "projects [SharePoint development in Visual Studio], saving string data"
  - "SharePoint projects, saving string data"
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Saving Data in Extensions of the SharePoint Project System
  При расширении системы проектов SharePoint можно сохранить строковые данные, которые должны оставаться неизменными после закрытия проекта SharePoint.  Обычно такие данные связаны с определенным элементом проекта или с самим проектом.  
  
 Если имеются данные, сохранять которые не требуется, можно добавить их в любой объект объектной модели средств SharePoint, в котором реализован интерфейс <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>.  Дополнительные сведения см. в разделе [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## Сохранение данных, связанных с элементом проекта  
 Если имеются данные, связанные с определенным элементом проекта SharePoint \(например, значение свойства, добавляемое в элемент проекта\), их можно сохранить в файл с расширением SPDATA для элемента проекта.  Для этого используйте свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>.  Данные, добавленные в это свойство, сохраняются в элементе **ExtensionData** в SPDATA\-файле элемента проекта.  Дополнительные сведения см. в разделе [ExtensionData Element](../sharepoint/extensiondata-element.md).  
  
 В следующем примере кода демонстрируется использование свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> для сохранения значения свойства \(которое является строкой\), определенного в настраиваемом типе элемента проекта SharePoint.  Данный пример в контексте полного примера см. в разделе [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#14)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#14)]  
  
## Сохранение данных, связанных с проектом  
 Если имеются данные на уровне проекта \(например, значение свойства, добавляемое в проекты SharePoint\), их можно сохранить в файл проекта \(с расширением CSPROJ или VBPROJ\) или файл пользовательских параметров проекта \(с расширением CSPROJ.USER или VBPROJ.USER\).  Выбор файла для сохранения данных зависит от того, как будут использоваться эти данные.  
  
-   Если требуется, чтобы данные были доступны всем разработчикам, открывающим проект SharePoint, сохраните их в файл проекта.  Этот файл всегда возвращается в базу данных системы управления версиями, поэтому содержащиеся в нем данные доступны другим разработчикам, извлекающим этот проект.  
  
-   Если требуется, чтобы данные были доступны только текущему разработчику, у которого проект SharePoint открыт в Visual Studio, сохраняйте их в файл пользовательских параметров проекта.  Этот файл обычно не возвращается в базу данных системы управления версиями, поэтому содержащиеся в нем данные не доступны другим разработчикам, извлекающим этот проект.  
  
### Сохранение данных в файл проекта  
 Чтобы сохранить данные в файл проекта, преобразуйте объект <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> в объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>, затем воспользуйтесь методом <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>.  В следующем примере кода показано использование этого метода для сохранения значения свойства проекта в файл проекта.  Данный пример в контексте полного примера см. в разделе [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#3)]
 [!code-vb[SpExt_SPCustomPrjProperty#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#3)]  
  
 Дополнительные сведения о преобразовании объектов <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> в другие типы объектной модели автоматизации или объектной модели интеграции Visual Studio см. в разделе [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### Сохранение данных в файл пользовательских параметров проекта  
 Чтобы сохранить данные в файл пользовательских параметров проекта, используйте свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  В следующем примере кода показано использование этого свойства для сохранения значения свойства проекта в файл пользовательских параметров проекта.  Данный пример в контексте полного примера см. в разделе [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#2)]
 [!code-vb[SpExt_SPCustomPrjProperty#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#2)]  
  
## См. также  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  