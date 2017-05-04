---
title: "ProjectItemFolder Element | Microsoft Docs"
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
  - "ProjectItemFolder element"
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# ProjectItemFolder Element
  Представляет сопоставляемую папку.  
  
## Синтаксис  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## Тип  
 **ProjectItemFolderType**  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|**Target**|Обязательный атрибут элемента **xs:string**.<br /><br /> Путь к папке в установке SharePoint, соответствующей сопоставленной папке, задается относительно корневой папки развертывания.  Корневая папка развертывания определяется типом развертывания, заданным атрибутом **Type**.<br /><br /> Дополнительные сведения см. в описаниях свойств **Deployment Path** и **Deployment Root** элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Обязательный атрибут элемента **xs:string**.<br /><br /> Тип развертывания сопоставленной папки.  Дополнительные сведения о возможных значениях см. в описании свойства **Deployment Type** элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint.  Это обязательный корневой элемент SPDATA\-файла.|  
  
## Заметки  
 Дополнительные сведения о сопоставленных папках см. в разделе [Практическое руководство. Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## См. также  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Практическое руководство. Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  