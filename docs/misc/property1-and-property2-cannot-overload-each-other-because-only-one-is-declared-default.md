---
title: "&quot;&lt;свойство1&gt;&quot; и &quot;&lt;свойство2&gt;&quot; не могут перегружать друг друга, т.&#160;к. только одно из них объявлено как Default. | Microsoft Docs"
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
  - "bc30361"
  - "vbc30361"
helpviewer_keywords: 
  - "BC30361"
ms.assetid: bac85b32-1a1f-4c43-817c-76e209cfeb8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;свойство1&gt;&quot; и &quot;&lt;свойство2&gt;&quot; не могут перегружать друг друга, т.&#160;к. только одно из них объявлено как Default.
Если свойство объявлено как `Default`, то все свойства, перегруженные для этого свойства, также должны быть объявлены как `Default`.  
  
 **Идентификатор ошибки:** BC30361  
  
### Исправление ошибки  
  
-   Убедитесь, что все перегруженные свойства объявлены как `Default`.  
  
## См. также  
 [Вопросы, связанные с перегрузкой процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)