---
title: "Сохранение данных в расширениях системы проектов SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 56cdfb95de6f0e5f8644ea3c73daacbf90e33a97
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>Сохранение данных в расширениях системы проектов SharePoint
  При расширении системы проектов SharePoint можно сохранить строковые данные, которые должны оставаться неизменными после закрытия проекта SharePoint. Данные обычно связана с определенным элементом проекта или сам проект.  
  
 Если у вас есть данные, которые необходимо сохранить, можно добавить данные к любому объекту в объектной модели инструментов SharePoint, реализующий <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> интерфейса. Дополнительные сведения см. в разделе [связывание пользовательских данных с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>Сохранение данных, связанный с элементом проекта  
 При наличии данных, связанный с данным элементом проекта SharePoint, например, значение свойства, добавьте в элемент проекта можно сохранить данные в файл с расширением SPDATA для элемента проекта. Чтобы сделать это, используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта. Данные, добавленные к этому свойству сохраняется в **ExtensionData** элемент SPDATA-файла для элемента проекта. Дополнительные сведения см. в разделе [ExtensionData-элемент](../sharepoint/extensiondata-element.md).  
  
 В следующем примере кода демонстрируется использование <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство, чтобы сохранить значение строкового свойства, определенные в настраиваемого типа элемента проекта SharePoint. Этот пример в контексте полного примера см. в разделе [как: добавить свойство в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>Сохранение данных, связанный с проектом  
 При наличии данных на уровне проекта, например, значение свойства, добавление в проекты SharePoint можно сохранить данные в файле проекта (CSPROJ-файл или VBPROJ-файле) или файл пользовательских параметров проекта (. файл csproj.user или. vbproj.user файла). Файл, выбранный для сохранения данных зависит от того, способ данных для использования.  
  
-   Если требуется, чтобы данные были доступны для всех разработчиков, откройте проект SharePoint, необходимо сохраните данные в файл проекта. Этот файл всегда возвращается базу данных управления версиями, чтобы данные в этот файл был доступен другим разработчикам, извлекающим этот проект.  
  
-   Если требуется, чтобы данные, которые будут доступны только текущему разработчику, открывшего проект SharePoint в Visual Studio, сохраните данные в файл пользовательских параметров проекта. Этот файл не проверяется обычно базу данных управления версиями, поэтому данные в этом файле не доступны другим разработчикам, извлекающим проекта.  
  
### <a name="saving-data-to-the-project-file"></a>Сохранение данных в файл проекта  
 Чтобы сохранить данные в файл проекта, преобразуйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> , а затем использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> метода. В следующем примере кода показано, как использовать этот метод для сохранения значения свойства проекта в файл проекта. Этот пример в контексте полного примера см. в разделе [как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Дополнительные сведения о преобразовании <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объектов для других типов в объектной модели автоматизации Visual Studio или объектной модели интеграции см [преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio ](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>Сохранение данных в файл пользовательских параметров проекта  
 Чтобы сохранить данные в файл пользовательских параметров проекта, используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объекта. В следующем примере кода показано, как использовать это свойство для сохранения значения свойства проекта в файл пользовательских параметров проекта. Этот пример в контексте полного примера см. в разделе [как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>См. также  
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Связывание пользовательских данных с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  