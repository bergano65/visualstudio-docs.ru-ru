---
title: Как выполнить Добавление свойства в проекты SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f898ffd70888f00b508223ec4d3c578cbc4d538
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869610"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Как выполнить Добавление свойства в проекты SharePoint
  Расширение проекта можно использовать для добавления свойства в любой проект SharePoint. Свойство отображается в **свойства** окно при выборе проекта в **обозревателе решений**.  
  
 Следующие шаги предполагают, что вы уже создали расширение проекта. Дополнительные сведения см. в разделе [Как Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Добавление свойства в проект SharePoint  
  
1.  Определение класса с открытое свойство, которое представляет свойство, которое вы добавляете в проекты SharePoint. Если вы хотите добавить несколько свойств, можно определить все свойства, в том же классе или в разных классах.  
  
2.  В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метод вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> реализации, дескриптор <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> событие *projectService* параметра.  
  
3.  В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> событий, добавьте экземпляр класса свойства <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> коллекцию параметра аргументов события.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как добавить два свойства для проектов SharePoint. Одно свойство данные сохраняются в файл пользовательских параметров проекта ( *. csproj.user* файл или *. vbproj.user* файла). Другие свойства данные сохраняются в файле проекта (*.csproj* файл или *.vbproj* файла).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understand-the-code"></a>Понимание кода  
 Чтобы убедиться, что тот же экземпляр `CustomProjectProperties` класса используется каждый раз <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> событием, в примере кода добавляется объект свойств в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство проекта первый, когда происходит это событие. Каждый раз, когда это событие повторяется, код получает этот объект. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство для связывания данных с проектами, см. в разделе [расширений средств сопоставления пользовательских данных с SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Чтобы сохранить изменения значений свойств, **задать** методы доступа свойств используют следующие API:  
  
- `CustomUserFileProperty` использует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> свойство для сохранения его значения в файл пользовательских параметров проекта.  
  
- `CustomProjectFileProperty` использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> метод, чтобы сохранить его значение в файл проекта.  
  
  Дополнительные сведения о сохранении данных в этих файлах см. в разделе [сохранения данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Указать поведение пользовательских свойств  
 Можно определить, как выглядит и ведет себя как пользовательское свойство **свойства** окна, применяя различные атрибуты из <xref:System.ComponentModel> пространство имен для определения свойства. Следующие атрибуты полезны во многих сценариях:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Указывает имя свойства, которое отображается в **свойства** окна.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Задает строку описания, который отображается в нижней части **свойства** окно при выборе свойства.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Задает значение по умолчанию свойства.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Задает настраиваемое преобразование между строкой, отображаемой в **свойства** окно и значение свойства, не являющегося строкой.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Указывает пользовательский редактор для изменения свойства.  
  
## <a name="compile-the-code"></a>Компиляция кода  
 В этом примере требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint
-    
-   Microsoft.VisualStudio.Shell
-     
-   Microsoft.VisualStudio.Shell.Interop
-     
-   Microsoft.VisualStudio.Shell.Interop.8.0
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также
 [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Практическое руководство. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Практическое руководство. Добавление пункта контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
