---
title: "Справочник по схеме элементов проектов SharePoint | Документы Microsoft"
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
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67f9d29ff18f4ec12653838d25dc3951a53757bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
  
  