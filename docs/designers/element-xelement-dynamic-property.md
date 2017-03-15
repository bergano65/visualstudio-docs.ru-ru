---
title: "Element (динамическое свойство XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Element"
apitype: "Assembly"
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Element (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Получает индексатор, который используется для получения экземпляра дочернего элемента, соответствующего указанному развернутому имени.  
  
## Синтаксис  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## Значение свойства\/возвращаемое значение  
 Индексатор типа `XElement Item(String expandedName)`.Этот индексатор берет параметр развернутого имени и возвращает соответствующее значение элемента <xref:System.Xml.Linq.XElement> или `null`, если элемента с таким именем не существует.  
  
## Заметки  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Element%2A> класса <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.  
  
## См. также  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)   
 [Элементы](../designers/elements-xelement-dynamic-property.md)