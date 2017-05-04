---
title: "ProjectOutputFile Element | Microsoft Docs"
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
  - "ProjectOutputFile element"
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# ProjectOutputFile Element
  Представляет выходные данные отдельного проекта для включения с элементом проекта при его развертывании в SharePoint.  
  
## Синтаксис  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## Тип  
 **ProjectOutputFileType**  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|**ProjectId**|Обязательный атрибут элемента **xs:string**.<br /><br /> GUID зависимого проекта, имеющий выходные данные, которые требуется включить.  Это значение соответствует элементу **ProjectGuid** в файле зависимого проекта.|  
|**ProjectPath**|Обязательный атрибут элемента **xs:string**.<br /><br /> Относительный путь, включая имя файла зависимого проекта, который содержит выходные данные, которые требуется включить.  Этот путь определяется относительно корневой папки проекта SharePoint, в которой содержится элемент проекта SharePoint.|  
|**Target**|Необязательный атрибут элемента **xs:string**.<br /><br /> Путь, где выполняется развертывание выходных файлов зависимого проекта на сервере SharePoint, задаваемый относительно корневой папки развертывания.  Корневая папка развертывания определяется типом развертывания, заданным атрибутом **Type**.<br /><br /> Дополнительные сведения см. в описаниях свойств **Deployment Path** и **Deployment Root** элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Обязательный атрибут элемента **xs:string**.<br /><br /> Тип развертывания, используемый для выходных данных зависимого проекта.  Дополнительные сведения о возможных значениях см. в описании свойства **Deployment Type** элементов проекта SharePoint в разделе [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Файлы](../sharepoint/files-element.md)|Задает файлы для включения с элементом проекта SharePoint при его развертывании в SharePoint.|  
  
## Заметки  
 Используйте элемент **ProjectOutputFile** для включения выходных данных проекта в развертывании элемента проекта SharePoint.  Можно указать другой проект или тот же проект, который содержит элемент проекта.  Дополнительные сведения см. в разделе [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## См. также  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  