---
title: "&quot;&lt;имя_типа&gt;&quot; не может использоваться как атрибут, так как содержит непереопределенные методы, помеченные как &quot;MustOverride&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31507"
  - "vbc31507"
helpviewer_keywords: 
  - "BC31507"
ms.assetid: 843643d3-3e81-4ce3-b4df-278882f3954d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_типа&gt;&quot; не может использоваться как атрибут, так как содержит непереопределенные методы, помеченные как &quot;MustOverride&quot;
Классы с методами `MustOverride` нельзя использовать в качестве атрибутов.  
  
 Члены `MustOverride` классов атрибутов можно использовать только в производных классах, переопределяющих эти члены.  
  
 **Идентификатор ошибки:** BC31507  
  
### Исправление ошибки  
  
1.  Удалите модификатор `MustOverride` из членов класса атрибутов.  
  
2.  Реализуйте члены `MustOverride` в производном классе и используйте этот класс в качестве атрибута.  
  
## См. также  
 <xref:System.AttributeUsageAttribute>   
 [НЕ В СБОРКЕ. Настраиваемые атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/d72d8a5c-8f64-4614-b15b-cad66845d047)