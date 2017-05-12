---
title: "ExtensionDataItem Element"
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
  - "ExtensionDataItem element"
ms.assetid: 6a5fe7eb-b433-42dc-bd50-4882b780e2fb
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ExtensionDataItem Element
  Представляет пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате ключ\/значение.  Ключ и значение должны быть строками.  
  
## Синтаксис  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|**Key**|Обязательный атрибут элемента **xs:string**.<br /><br /> Ключ, используемый для хранения и извлечения элемента данных.|  
|**Value**|Обязательный атрибут элемента **xs:string**.<br /><br /> Значение элемента данных.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.|  
  
## Заметки  
 При связывании пользовательских данных с элементом проекта SharePoint с помощью свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Visual Studio сохраняет данные нового элемента **ExtensionDataItem** в SPDATA\-файле элемента проекта.  Дополнительные сведения см. в разделе [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## См. также  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  