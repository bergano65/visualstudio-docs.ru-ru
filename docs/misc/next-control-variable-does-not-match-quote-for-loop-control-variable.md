---
title: "Управляющая переменная &quot;Next&quot; не соответствует управляющей переменной цикла &quot;For&quot; | Microsoft Docs"
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
  - "vbc30976"
  - "bc30976"
helpviewer_keywords: 
  - "BC30976"
ms.assetid: 87c2d464-43bf-426f-b78b-7bc07ba171e6
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Управляющая переменная &quot;Next&quot; не соответствует управляющей переменной цикла &quot;For&quot;
Управляющая переменная в операторе `Next` цикла `For...Next` должна соответствовать переменной в операторе `For`.  
  
 **Идентификатор ошибки:** BC30976  
  
### Исправление ошибки  
  
-   Проверьте правильность написания переменной в операторе `Next` и соответствующем операторе `For`.  
  
-   Убедитесь в том, что ни одна из частей внешнего цикла не была случайно удалена.  
  
-   Если цикл входит в набор вложенных циклов, убедитесь в том, что каждый цикл завершается должным образом.  
  
## См. также  
 [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)