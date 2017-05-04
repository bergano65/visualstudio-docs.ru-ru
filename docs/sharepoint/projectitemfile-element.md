---
title: "ProjectItemFile Element | Microsoft Docs"
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
  - "ProjectItemFile element"
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ProjectItemFile Element
  Представляет файл SharePoint, например, файл элемента "Компонент", включаемый в элемент проекта при развертывании в SharePoint.  
  
## Синтаксис  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## Тип  
 **ProjectItemFileType**  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|**Source**|Обязательный атрибут элемента **xs:string**.<br /><br /> Имя файла, который развертывается с элементом проекта.|  
|**Target**|Необязательный атрибут элемента **xs:string**.<br /><br /> Путь для развертывания файла на сервере SharePoint Server, который задается относительно корневой папки развертывания.  Корневая папка развертывания определяется типом развертывания, заданным атрибутом **Type**.  Если атрибут **Target** не указан, файл будет развернут в папку с именем, указанным в атрибуте **Source**.<br /><br /> Дополнительные сведения см. в описаниях свойств **Deployment Path** и **Deployment Root** элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Обязательный атрибут элемента **xs:string**.<br /><br /> Тип развертывания файла.  Дополнительные сведения о возможных значениях см. в описании свойства **Deployment Type** элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Файлы](../sharepoint/files-element.md)|Задает файлы для включения с элементом проекта SharePoint при его развертывании в SharePoint.|  
  
## Заметки  
 Файлы SharePoint, на которые обычно имеются ссылки в элементах **ProjectItemFile**, включают файлы элементов компонента \(Elements.xml\), файлы схемы для определений списков \(Schema.xml\) и файлы определения веб\-части для веб\-части \(файлы с расширением WEBPART\).  
  
## Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## См. также  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  