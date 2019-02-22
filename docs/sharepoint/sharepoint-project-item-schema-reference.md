---
title: Справочник по схеме элементов проектов SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc15ff5c384ec63f99ed50a5f3c700efd7ba3c18
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608725"
---
# <a name="sharepoint-project-item-schema-reference"></a>Справочник по схеме для элемента проекта SharePoint
  Visual Studio использует схему элемента проекта SharePoint для проверки содержимого *.spdata* файлов. *.Spdata* файл определяет содержимое и поведение элемента проекта SharePoint. Дополнительные сведения о содержимом элементов проекта SharePoint, см. в разделе [создание элементов, шаблоны и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Схема элемента проекта SharePoint, называется ProjectItemModelSchema.xsd и устанавливается по умолчанию в папку % Program Files (x86)%\Microsoft 11.0\Xml\Schemas Visual Studio.

 Корневой элемент — [ProjectItem](../sharepoint/projectitem-element.md) элемент. Ниже перечислены все элементы, определенные схемой.

|Элемент|Описание:|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Представляет коллекцию пользовательских элементов данных, которые связаны с элементом проекта SharePoint.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Представляет пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате ключ/значение. Ключ и значение должны быть строками.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Представляет коллекцию значений свойств, которые входят в состав компонентом при его развертывании в SharePoint. После развертывания функции значения свойств можно использовать в коде.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Представляет настраиваемое свойство, которое входит в состав компонентом при его развертывании в SharePoint. После развертывания функции можно использовать свойство в коде.|
|[Файлы](../sharepoint/files-element.md)|Указывает файлы для развертывания с элементом проекта SharePoint, такие как файл элемента компонента или выходных данных проекта.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Представляет файл SharePoint, такие как файл элемента компонента, для включения с элементом проекта при его развертывании в SharePoint.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Представляет сопоставленную папку.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Представляет выходные данные проекта для включения с элементом проекта при его развертывании в SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Представляет элемент управления ASPX или веб-части, которое обозначается как безопасные для любого доступа пользователя к любой странице ASPX на сайте SharePoint.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Представляет коллекцию элементов управления ASPX и веб-частей, отмеченных как безопасные для любого доступа пользователя к любой странице ASPX на сайте SharePoint.|

## <a name="see-also"></a>См. также
- [Создание шаблонов элементов и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
