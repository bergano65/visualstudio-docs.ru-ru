---
title: Сохранение данных в расширениях системы проектов SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52b04490a646c7ced27d4a2d7f2344e27cbbae8b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082767"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Сохранение данных в расширениях системы проектов SharePoint
  При расширении системы проектов SharePoint, можно сохранить строковые данные, которые должны оставаться неизменными после закрытия проекта SharePoint. Данные обычно связана с определенным элементом проекта или сам проект.

 Если у вас есть данные, которые не требуется сохранять, можно добавить данные к любому объекту в объектной модели инструментов SharePoint, реализующий <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> интерфейс. Дополнительные сведения см. в разделе [расширений средств сопоставления пользовательских данных с SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Сохранить данные, связанные с элементом проекта
 Если у вас есть данные, связанные с данным элементом проекта SharePoint, например, значение свойства, добавляемого элемента проекта, можно сохранить данные для *.spdata* файла элемента проекта. Чтобы сделать это, используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта. Данные, добавляемые к этому свойству сохраняется в **ExtensionData** элемент в *.spdata* файла элемента проекта. Дополнительные сведения см. в разделе [элемент ExtensionData](../sharepoint/extensiondata-element.md).

 В следующем примере кода демонстрируется использование <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство для сохранения значения свойства строки, которая определена в настраиваемого типа элемента проекта SharePoint. Этот пример в контексте полного примера см. в разделе [как: Добавление свойства в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>Сохранить данные, связанные с проектом
 При наличии данных на уровне проекта, например, значение свойства, которое вы добавляете в проекты SharePoint можно сохранить данные в файл проекта ( *.csproj* файл или *.vbproj* файл) или параметр проекта пользователя файл ( *. csproj.user* файл или *. vbproj.user* файла). Файл, который вы решили сохранить данные в зависит от того, как требуется, чтобы данные для использования.

- Если требуется, чтобы данные были доступны всем разработчикам, откройте проект SharePoint, сохраните данные в файл проекта. Этот файл всегда возвращается базу данных управления версиями, поэтому данные в этот файл доступен другим разработчикам, извлекать проект.

- Если требуется, чтобы данные были доступны только текущему разработчику, открывшего проект SharePoint в Visual Studio, сохраните данные в файл пользовательских параметров проекта. Этот файл не возвращен обычно для баз данных, поэтому данные в этом файле недоступно другим разработчикам, извлекать проект.

### <a name="save-data-to-the-project-file"></a>Сохранить данные в файл проекта
 Чтобы сохранить данные в файл проекта, преобразуйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> , а затем использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> метод. В следующем примере кода показано, как использовать этот метод для сохранения значения свойства проекта в файл проекта. Этот пример, в контексте большего примера, см. в разделе [как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 Дополнительные сведения о преобразовании <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объектов для других типов в объектной модели автоматизации Visual Studio или объектной модели интеграции см. в разделе [преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Сохранить данные в файл пользовательских параметров проекта
 Чтобы сохранить данные в файл пользовательских параметров проекта, используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объекта. В следующем примере кода показано, как использовать это свойство для сохранения значения свойства проекта в файл пользовательских параметров проекта. Этот пример, в контексте большего примера, см. в разделе [как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>См. также
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Связывать пользовательские данные с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
