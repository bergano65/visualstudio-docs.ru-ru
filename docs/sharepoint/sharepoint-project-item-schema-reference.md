---
title: "SharePoint Project Item Schema Reference | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "FeatureProperty element"
  - "SafeControls element"
  - "SafeControl element"
  - ".spdata files"
  - "ExtensionData element"
  - "FeatureProperties element"
  - "ProjectOutputFile element"
  - "Files element"
  - "ProjectItemFolder element"
  - "ProjectItemFile element"
  - "ExtensionDataItem element"
  - "ProjectItem element"
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint Project Item Schema Reference
  Visual Studio использует схему элементов проекта SharePoint для проверки содержимого SPDATA\-файлов.  SPDATA\-файл указывает содержимое и поведение элемента проекта SharePoint.  Дополнительные сведения о содержимом элементов проектов SharePoint см. в разделе [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Схема элементов проекта SharePoint имеет имя ProjectItemModelSchema.xsd и по умолчанию установлена в папке %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas.  
  
 Корневым элементом является элемент [ProjectItem](../sharepoint/projectitem-element.md).  В следующей таблице описаны все элементы, определенные схемой.  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Представляет пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате ключ\/значение.  Ключ и значение должны быть строками.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Представляет коллекцию значений свойства, включенных в "Компонент" при развертывании в SharePoint.  После развертывания "Компонента", доступ к значениям свойства можно получить через код.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Представляет пользовательское свойство, включенное в "Компонент" при развертывании в SharePoint.  После развертывания "Компонента", доступ к свойству можно получить через код.|  
|[Файлы](../sharepoint/files-element.md)|Указывает файлы для развертывания с помощью элемента проекта SharePoint, например, файл элемента "Компонент" или выходные данные проекта.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Представляет файл SharePoint, например, файл элемента "Компонент", включаемый в элемент проекта при развертывании в SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Представляет сопоставляемую папку.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Представляет выходные данные проекта, включаемые в элемент проекта при его развертывании в SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Представляет элемент управления ASPX или веб\-часть, отмеченную как безопасная, с доступом для любых пользователей на любой странице ASPX сайта SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Представляет коллекцию элементов управления ASPX или веб\-частей, отмеченных как безопасные, с доступом для любых пользователей на любой странице ASPX сайта SharePoint.|  
  
## См. также  
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  