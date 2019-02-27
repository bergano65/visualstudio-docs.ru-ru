---
title: Практическое руководство. Добавление свойства в расширение элемента проекта SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc2c0588fa3078a805f9804263afcf521ae72ed
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644436"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Практическое руководство. Добавление свойства в расширение элемента проекта SharePoint
  Расширение элемента проекта можно использовать для добавления свойства к любому элементу проекта SharePoint, уже установлен в Visual Studio. Свойство отображается в **свойства** окно при выборе элемента проекта в **обозревателе решений**.

 Следующие шаги предполагают, что вы уже создали в расширение элемента проекта. Дополнительные сведения см. в разделе [Как Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Добавление свойства в расширение элемента проекта

1.  Определение класса с открытое свойство, которое представляет свойство, добавляемый тип элемента проекта. Если вы хотите добавить несколько свойств для типа элемента проекта, можно определить все свойства, в том же классе или в разных классах.

2.  В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метод вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> реализации, дескриптор <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> *событие* параметра.

3.  В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событий, добавьте экземпляр класса свойства <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> коллекцию параметра аргументов события.

## <a name="example"></a>Пример
 В следующем примере кода показано, как добавить свойство с именем **примером свойства** на элемент проекта приемника событий.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Понимание кода
 Чтобы убедиться, что тот же экземпляр `CustomProperties` класса используется каждый раз <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событием, в примере кода добавляется объект свойств в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства проекта, когда это событие происходит впервые. Каждый раз, когда это событие повторяется, код получает этот объект. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство для связывания данных с элементами проекта см. в разделе [расширений средств сопоставления пользовательских данных с SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Для сохранения изменений значение свойства, **задать** метод доступа для `ExampleProperty` сохраняет новое значение для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> , свойство, связанное с объектом. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство для сохранения данных с помощью элементов проекта, см. в разделе [сохранения данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Указать поведение пользовательских свойств
 Можно определить, как выглядит и ведет себя как пользовательское свойство **свойства** окна, применяя различные атрибуты из <xref:System.ComponentModel> пространство имен для определения свойства. Следующие атрибуты полезны во многих сценариях:

-   <xref:System.ComponentModel.DisplayNameAttribute>: Указывает имя свойства, которое отображается в **свойства** окна.

-   <xref:System.ComponentModel.DescriptionAttribute>: Задает строку описания, который отображается в нижней части **свойства** окно при выборе свойства.

-   <xref:System.ComponentModel.DefaultValueAttribute>: Задает значение по умолчанию свойства.

-   <xref:System.ComponentModel.TypeConverterAttribute>: Задает настраиваемое преобразование между строкой, отображаемой в **свойства** окно и значение свойства, не являющегося строкой.

-   <xref:System.ComponentModel.EditorAttribute>: Указывает пользовательский редактор для изменения свойства.

## <a name="compile-the-code"></a>Компиляция кода
 Для этих примеров требуются проект библиотеки классов с помощью ссылки на следующие сборки:

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Практическое руководство. Добавление пункта контекстного меню в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Пошаговое руководство: Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
