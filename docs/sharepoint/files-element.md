---
title: "Files Element | Microsoft Docs"
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
  - "Files element"
ms.assetid: 3c611d5b-28f1-48a7-a068-63e01fa2f3aa
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Files Element
  Указывает файлы для развертывания с элементом проекта SharePoint, такие как файлы элемента Feature и выходные файлы зависимых проектов, отличных от проектов SharePoint.  
  
## Синтаксис  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## Тип  
 **FileCollectionType**  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Необязательный элемент **ProjectItemFileType**.<br /><br /> Представляет файл SharePoint, например, файл элемента "Компонент", включаемый в элемент проекта при развертывании в SharePoint.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Необязательный элемент **ProjectOutputFileType**.<br /><br /> Представляет выходные данные проекта, включаемые в элемент проекта при его развертывании в SharePoint.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint.  Это обязательный корневой элемент SPDATA\-файла.|  
  
## Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## См. также  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  