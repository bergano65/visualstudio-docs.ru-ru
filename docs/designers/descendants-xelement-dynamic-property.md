---
title: "Descendants (динамическое свойство XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Descendants (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Возвращает индексатор, который используется для получения всех элементов\-потомков текущего элемента, соответствующих заданному развернутому имени.  
  
## Синтаксис  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## Значение свойства\/возвращаемое значение  
 Индексатор типа `IEnumerable<XElement> Item(String expandedName)`.Этот индексатор принимает развернутое имя указанных элементов\-потомков и возвращает соответствующие дочерние элементы в коллекции <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## Заметки  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> класса <xref:System.Xml.Linq.XContainer>.  
  
 Элементы в возвращаемой коллекции располагаются в порядке исходного XML\-документа.  
  
 В данном свойстве используется отложенное выполнение.  
  
## См. также  
 [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)   
 [Элементы](../designers/elements-xelement-dynamic-property.md)