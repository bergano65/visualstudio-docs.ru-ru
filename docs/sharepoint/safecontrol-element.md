---
title: "SafeControl Element"
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
  - "SafeControl element"
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControl Element
  Представляет элемент управления ASPX или веб\-часть, отмеченную как безопасная, с доступом для любых пользователей на любой странице ASPX сайта SharePoint.  
  
## Синтаксис  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|**Assembly**|Необязательный атрибут элемента **xs:string**.<br /><br /> Имя сборки, в которой определен элемент управления ASPX или веб\-части.  По умолчанию этот атрибут использует замещаемый параметр **$SharePoint.Project.AssemblyFullName$** для имени сборки.  Дополнительные сведения см. в разделе [Подстановочные параметры](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Необязательный атрибут элемента **xs:boolean**.<br /><br /> Указывает, являются ли элемент управления ASPX или веб\-часть безопасными при доступе ненадежных пользователей.|  
|**IsSafeAgainstScript**|Необязательный атрибут элемента **xs:boolean**.<br /><br /> Указывает, могут ли ненадежные пользователи просмотреть или изменять свойства элемента управления ASPX или веб\-части.|  
|**Name**|Необязательный атрибут элемента **xs:string**.<br /><br /> Имя этой записи безопасного элемента управления в коллекции.|  
|**Namespace**|Необязательный атрибут элемента **xs:string**.<br /><br /> Пространство имен элемента управления ASPX или веб\-части.|  
|**TypeName**|Необязательный атрибут элемента **xs:string**.<br /><br /> Имя типа элемента управления ASPX или веб\-части.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Представляет коллекцию элементов управления ASPX или веб\-частей, отмеченных как безопасные, с доступом для любых пользователей на любой странице ASPX сайта SharePoint.|  
  
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
  
  