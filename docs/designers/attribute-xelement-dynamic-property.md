---
title: "Attribute (динамическое свойство XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Attribute (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Возвращает индексатор, используемый для получения экземпляра атрибута, соответствующего указанному развернутому имени.  
  
## Синтаксис  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## Значение свойства\/возвращаемое значение  
 Индексатор типа `XAttribute Item(String expandedName)`.Данный индексатор принимает развернутое имя указанного атрибута и возвращает соответствующий <xref:System.Xml.Linq.XAttribute> или значение `null`, если не существует атрибута с указанным именем.  
  
## Заметки  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XElement.Attribute%2A> класса <xref:System.Xml.Linq.XElement?displayProperty=fullName>.  
  
## См. также  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)   
 [Значение](../designers/value-xattribute-dynamic-property.md)