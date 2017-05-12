---
title: "ExtensionData Element"
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
  - "ExtensionData element"
ms.assetid: caf6843b-dcf5-4688-a9eb-a424aae1beab
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ExtensionData Element
  Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.  
  
## Синтаксис  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Необязательный элемент.<br /><br /> Представляет пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате ключ\/значение.  Ключ и значение должны быть строками.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint.  Это обязательный корневой элемент SPDATA\-файла.|  
  
## Заметки  
 При связывании пользовательских данных с элементом проекта SharePoint с помощью свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Visual Studio сохраняет данные элемента **ExtensionData** в SPDATA\-файле элемента проекта.  Дополнительные сведения см. в разделе [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## См. также  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  