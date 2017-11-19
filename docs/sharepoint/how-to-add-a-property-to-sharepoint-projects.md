---
title: "Как: Добавление свойства в проекты SharePoint | Документы Microsoft"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e43e4921a32cc84b8384950e88c589b1bbddc31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Практическое руководство. Добавление свойства в проекты SharePoint
  Расширение проекта можно использовать, чтобы добавить свойство в любой проект SharePoint. Это свойство отображается в **свойства** окна, когда проект выбран в **обозревателе решений**.  
  
 Следующие шаги предполагают, что вы уже создали расширения проекта. Дополнительные сведения см. в разделе [как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Добавление свойства в проект SharePoint  
  
1.  Определите класс с открытым свойством, которое представляет свойство, добавляемое в проекты SharePoint. Если требуется добавить несколько свойств, можно определить все свойства в том же классе или в разных классов.  
  
2.  В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метод вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> реализацию, дескриптор <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> событие *projectService* параметра.  
  
3.  В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> событий, добавьте экземпляр класса свойств <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> коллекцию параметра аргументов события.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как добавить два свойства для проектов SharePoint. Одно из свойств данные сохраняются в файл пользовательских параметров проекта (. файл csproj.user или. vbproj.user файла). Другие свойства данные сохраняются в файле проекта (CSPROJ-файл или VBPROJ).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>Общие сведения о коде  
 Чтобы убедиться, что тот же экземпляр `CustomProjectProperties` класса используется каждый раз <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> происходит событие, пример кода добавляет объект свойств в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство проекта первый, когда происходит данное событие. Код получает этот объект, когда происходит данное событие. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство для связывания данных с проектами, в разделе [связывание пользовательских данных с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Чтобы сохранить изменения значений свойств **задать** методы доступа для свойств используют следующие API:  
  
-   `CustomUserFileProperty`использует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> свойство для сохранения своего значения в файл пользовательских параметров проекта.  
  
-   `CustomProjectFileProperty`использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> метод для сохранения своего значения в файл проекта.  
  
 Дополнительные сведения о сохранении данных в этих файлах см. в разделе [сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Задание поведения пользовательских свойств  
 Можно определить как пользовательское свойство выглядит и работает в **свойства** окна путем применения атрибутов из <xref:System.ComponentModel> пространство имен для определения свойства. Во многих сценариях полезны следующие атрибуты:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Задает имя свойства, которое отображается в **свойства** окна.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Задает строку описания, которое отображается в нижней части **свойства** окно при выборе данного свойства.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Задает значение свойства по умолчанию.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Задает настраиваемое преобразование между строкой, которая отображается в **свойства** окна и значение свойства, не являющегося строкой.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Задает пользовательский редактор для изменения свойства.  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Как: Добавление пункта контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  