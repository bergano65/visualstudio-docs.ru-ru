---
title: Как выполнить Добавить свойство в тип элемента проекта SharePoint пользовательских | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ca3bfbf6ecd773f0a7c3147a44eb02a5c260764b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872798"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Как выполнить Добавление свойства в пользовательский тип элемента проекта SharePoint
  При определении настраиваемого типа элемента проекта SharePoint, можно добавить свойство к элементу проекта. Свойство отображается в **свойства** окно при выборе элемента проекта в **обозревателе решений**.  
  
 Следующие шаги предполагают, что уже было определено собственный тип элемента проекта SharePoint. Дополнительные сведения см. в разделе [Как Определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Добавление свойства в определении типа элемента проекта  
  
1.  Определение класса с открытое свойство, которое представляет свойство, которое вы добавляете для пользовательского типа элемента проекта. Если вы хотите добавить несколько свойств для пользовательского типа элемента проекта, можно определить все свойства, в том же классе или в разных классах.  
  
2.  В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> реализации, дескриптор <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событие *projectItemTypeDefinition* параметра.  
  
3.  В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событий, добавьте экземпляр пользовательского класса свойств для <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> коллекцию параметра аргументов события.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как добавить свойство с именем **примером свойства** для пользовательского типа элемента проекта.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understand-the-code"></a>Понимание кода  
 Чтобы убедиться, что тот же экземпляр `CustomProperties` класса используется каждый раз <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событием, в примере кода сохраняет объект свойств в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства проекта, когда это событие происходит впервые. Каждый раз, когда это событие повторяется, код получает этот объект. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство для сохранения данных с элементами проекта см. в разделе [расширений средств сопоставления пользовательских данных с SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Для сохранения изменений значение свойства, **задать** метод доступа для `ExampleProperty` сохраняет новое значение для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> , свойство, связанное с объектом. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство для сохранения данных с помощью элементов проекта, см. в разделе [сохранения данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Указать поведение пользовательских свойств  
 Можно определить, как выглядит и ведет себя как пользовательское свойство **свойства** окна, применяя различные атрибуты из <xref:System.ComponentModel> пространство имен для определения свойства. Следующие атрибуты полезны во многих сценариях:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Указывает имя свойства, которое отображается в **свойства** окна.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Задает строку описания, который отображается в нижней части **свойства** окно при выборе свойства.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Задает значение по умолчанию свойства.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Задает настраиваемое преобразование между строкой, отображаемой в **свойства** окно и значение свойства, не являющегося строкой.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Указывает пользовательский редактор для изменения свойства.  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Эти примеры кода требуется проект библиотеки классов с помощью ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Развернуть элемент проекта  
 Чтобы другие разработчики могли использовать созданный элемент проекта, создайте шаблон проекта или шаблона элемента проекта. Дополнительные сведения см. в разделе [создание элементов, шаблоны и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Чтобы развернуть элемент проекта, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки, шаблон и другие файлы, которые вы хотите распространять вместе с элементом проекта. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также
 [Практическое руководство. Определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Практическое руководство. Добавление пункта контекстного меню в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
