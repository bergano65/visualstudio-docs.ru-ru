---
title: "&quot;&lt;член&gt;&quot;, неявно объявленный для &quot;&lt;имя_события&gt;&quot;, не может затенять метод &quot;MustOverride&quot; в базе &lt;класс&gt; &quot;&lt;имя_класса&gt;&quot; | Microsoft Docs"
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
  - "vbc31413"
  - "bc31413"
helpviewer_keywords: 
  - "BC31413"
ms.assetid: 071706ce-a394-48b6-9afa-751cb50b2576
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;член&gt;&quot;, неявно объявленный для &quot;&lt;имя_события&gt;&quot;, не может затенять метод &quot;MustOverride&quot; в базе &lt;класс&gt; &quot;&lt;имя_класса&gt;&quot;
В указанном событии неявным образом объявлен член, имя которого совпадает с именем метода, объявленного с модификатором `MustOverride`.  
  
 **Идентификатор ошибки:** BC31413  
  
### Исправление ошибки  
  
-   Удалите модификатор `MustOverride` из метода в базовом классе или присвойте свойству или методу уникальное имя.  
  
## См. также  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)