---
title: "FeatureProperty Element"
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
ms.assetid: 36a771a6-98d0-4a40-a278-d76baea82452
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# FeatureProperty Element
  Представляет пользовательское свойство, включенное в "Компонент" при развертывании в SharePoint.  После развертывания "Компонента", доступ к свойству можно получить через код.  
  
## Синтаксис  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|**Key**|Обязательный атрибут элемента **xs:string**.<br /><br /> Ключ, используемый для хранения и извлечения значения свойства.  Каждое свойство должно иметь ключ, который является уникальным в пределах компонента.|  
|**Value**|Обязательный атрибут элемента **xs:string**.<br /><br /> Значение свойства.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Представляет коллекцию значений свойства, включенных в "Компонент" при развертывании в SharePoint.|  
  
## Заметки  
 Дополнительные сведения о свойствах Feature см. в разделе [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
  
  