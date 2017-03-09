---
title: "&quot;&lt;имя_метода&gt;&quot; не может сделать теневым метод, объявленный как &quot;MustOverride&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31404"
  - "bc31404"
helpviewer_keywords: 
  - "BC31404"
ms.assetid: 3e7bb4a0-14af-46ba-bc62-2234c16f1827
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_метода&gt;&quot; не может сделать теневым метод, объявленный как &quot;MustOverride&quot;
Свойство или метод с модификатором `MustOverride` и таким же именем объявлено в производном классе.  
  
 **Идентификатор ошибки:** BC31404  
  
### Исправление ошибки  
  
1.  Добавьте модификатор `Overrides` к переопределяемому свойству или методу производного класса.  
  
2.  Удалите модификатор `MustOverride` из свойства или метода базового класса.  
  
## См. также  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)