---
title: "&quot;&lt;имя_типа&gt;&quot; не может переобъявлять метод &quot;MustOverride&quot;, неявно объявленный для свойства &quot;&lt;имя_свойства&gt;&quot; в &lt;тип&gt; &quot;&lt;имя_типа&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31416"
  - "vbc31416"
helpviewer_keywords: 
  - "BC31416"
ms.assetid: a52aee3c-a19e-412d-bb91-ef1b79e8675f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_типа&gt;&quot; не может переобъявлять метод &quot;MustOverride&quot;, неявно объявленный для свойства &quot;&lt;имя_свойства&gt;&quot; в &lt;тип&gt; &quot;&lt;имя_типа&gt;&quot;
Имя указанного метода конфликтует с методом `MustOverride`, который был неявно создан свойством базового класса. Например, если объявляется свойство с именем `Prop1`, компилятор создает неявные процедуры `get_Prop1` и `set_Prop1`.  
  
 **Идентификатор ошибки:** BC31416  
  
### Исправление ошибки  
  
1.  Присвойте методу уникальное имя.  
  
2.  Удалите модификатор `MustOverride` из свойства базового класса.  
  
## См. также  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)