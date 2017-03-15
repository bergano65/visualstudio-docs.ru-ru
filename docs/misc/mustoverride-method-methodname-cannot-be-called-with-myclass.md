---
title: "Метод &quot;&lt;имя_метода&gt;&quot;, помеченный как MustOverride, не может вызываться с помощью MyClass. | Microsoft Docs"
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
  - "bc30614"
  - "vbc30614"
helpviewer_keywords: 
  - "BC30614"
ms.assetid: fc57af41-1552-46d1-9727-341f1835e661
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &quot;&lt;имя_метода&gt;&quot;, помеченный как MustOverride, не может вызываться с помощью MyClass.
`MyClass` является эквивалентом `Me`, но все вызовы методов в нем рассматриваются, как если бы вызываемый метод был `NotOverridable`.  
  
 **Идентификатор ошибки**: BC30614  
  
### Исправление ошибки  
  
-   Удалите модификатор `MustOverride` или объявите метод в базовом классе, а затем выполните наследование и переопределение этого класса.  
  
## См. также  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)