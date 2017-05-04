---
title: "SafeControls Element | Microsoft Docs"
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
  - "SafeControls element"
ms.assetid: f5ffdbbe-cf85-4e5a-9d39-3cd4462f2a0e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControls Element
  Представляет коллекцию элементов управления ASPX или веб\-частей, отмеченных как безопасные, с доступом для любых пользователей на любой странице ASPX сайта SharePoint.  
  
## Синтаксис  
  
```  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Необязательный элемент.<br /><br /> Представляет элемент управления ASPX или веб\-часть, отмеченную как безопасная, с доступом для любых пользователей на любой странице ASPX сайта SharePoint.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint.  Это обязательный корневой элемент SPDATA\-файла.|  
  
## Заметки  
 Дополнительные сведения об безопасных элементах управления см. в разделе [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
  
  