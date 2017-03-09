---
title: "Тип &quot;&lt;имя_типа&gt;&quot; должен быть объявлен как &quot;MustInherit&quot;, так как он содержит методы, объявленные как &quot;MustOverride&quot;. | Microsoft Docs"
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
  - "vbc31411"
  - "bc31411"
helpviewer_keywords: 
  - "BC31411"
ms.assetid: 5a9f4c57-a4b8-45f5-8273-b7caa689a170
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_типа&gt;&quot; должен быть объявлен как &quot;MustInherit&quot;, так как он содержит методы, объявленные как &quot;MustOverride&quot;.
Типы, содержащие члены `MustOverride`, должны быть объявлены как `MustInherit`.  
  
 **Идентификатор ошибки:** BC31411  
  
### Исправление ошибки  
  
-   Добавьте в тип модификатор `MustInherit`.  
  
## См. также  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)