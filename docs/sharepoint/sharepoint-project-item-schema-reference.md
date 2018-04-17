---
title: Справочник по схеме элементов проектов SharePoint | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b039b1cf31a04a24819b03114c661a3ab1b108a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sharepoint-project-item-schema-reference"></a>Справочные материалы по схеме элементов проектов SharePoint
  Visual Studio использует схему элемента проекта SharePoint для проверки содержимого SPDATA-файлы. SPDATA-файл указывает содержимое и поведение элемента проекта SharePoint. Дополнительные сведения о содержимом элементов проектов SharePoint см. в разделе [Создание шаблонов элементов и проектов для элементов проекта SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Схема элемента проекта SharePoint с именем ProjectItemModelSchema.xsd и устанавливается по умолчанию в папке % Program Files (x86)%\Microsoft 11.0\Xml\Schemas Visual Studio.  
  
 Корневой элемент — [ProjectItem](../sharepoint/projectitem-element.md) элемента. В следующей таблице описаны все элементы, определенные в схеме.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Представляет пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате ключ значение. Ключ и значение должны быть строками.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Представляет коллекцию значений свойств, которые входят в состав компонентом при его развертывании в SharePoint. После развертывания функции значения свойств можно использовать в коде.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Представляет пользовательское свойство, которое входит в состав компонентом при его развертывании в SharePoint. После развертывания функции свойства можно использовать в коде.|  
|[Файлы](../sharepoint/files-element.md)|Указывает файлы для развертывания с элементом проекта SharePoint, такие как файл элемента компонента или выходные данные проекта.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Представляет файл SharePoint, таких как файл элемента компонента, для включения с элементом проекта при его развертывании в SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Представляет сопоставленную папку.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Представляет выходные данные проекта для включения с элементом проекта при его развертывании в SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Представляет элемент управления ASPX или веб-части, которые обозначены как безопасные для любому пользователю получить доступ к любой странице ASPX на сайте SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Представляет коллекцию элементов управления ASPX и веб-частей, отмеченных как безопасные для любому пользователю получить доступ к любой странице ASPX на сайте SharePoint.|  
  
## <a name="see-also"></a>См. также  
 [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  