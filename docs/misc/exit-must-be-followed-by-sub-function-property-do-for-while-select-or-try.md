---
title: "После оператора &quot;Exit&quot; должно быть указано ключевое слово &quot;Sub&quot;, &quot;Function&quot;, &quot;Property&quot;, &quot;Do&quot;, &quot;For&quot;, &quot;While&quot;, &quot;Select&quot; или &quot;Try&quot;. | Microsoft Docs"
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
  - "bc30240"
  - "vbc30240"
helpviewer_keywords: 
  - "BC30240"
ms.assetid: 91078689-f4bf-4331-a475-10bc9fe7cd0c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# После оператора &quot;Exit&quot; должно быть указано ключевое слово &quot;Sub&quot;, &quot;Function&quot;, &quot;Property&quot;, &quot;Do&quot;, &quot;For&quot;, &quot;While&quot;, &quot;Select&quot; или &quot;Try&quot;.
Оператор `Exit` содержит недопустимое ключевое слово.`Exit` должен указывать блок, из которого управление должно быть передано оператору после блока; например `End While`.  
  
 **Идентификатор ошибки:** BC30240  
  
### Исправление ошибки  
  
-   Добавьте допустимое ключевое слово после `Exit` или удалите оператор `Exit`.  
  
## См. также  
 [Оператор Exit](/dotnet/visual-basic/language-reference/statements/exit-statement)