---
title: "Xml (динамическое свойство XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Xml"
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Xml (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Возвращает неформатированное XML\-содержимое элемента.  
  
## Синтаксис  
  
```  
elem.Xml  
```  
  
## Значение свойства или возвращаемое значение  
 Значение <xref:System.String>, представляющее неформатированное XML\-содержимое элемента.  
  
## Заметки  
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> класса <xref:System.Xml.Linq.XNode?displayProperty=fullName> с параметром `SaveOptions`, установленным равным <xref:System.Xml.Linq.SaveOptions>.  
  
## См. также  
 [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)   
 [Значение](../designers/value-xelement-dynamic-property.md)