---
title: "Модули не могут быть универсальными | Microsoft Docs"
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
  - "BC32073"
  - "vbc32073"
helpviewer_keywords: 
  - "BC32073"
ms.assetid: 47246e2b-51d4-4a10-a3ac-bc77b44fa2ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Модули не могут быть универсальными
Оператор `Module` использует ключевое слово `Of` для представления параметров универсального типа.  
  
 Можно определять и использовать универсальные классы, структуры, интерфейсы, процедуры и делегаты. Нельзя определить универсальные модули.  
  
 **Идентификатор ошибки:** BC32073  
  
### Исправление ошибки  
  
1.  Удалите ключевое слово `Of` из оператора `Module`.  
  
2.  Если вы хотите использовать функциональность универсального модуля, наилучшим приближением является универсальный класс. Используйте [Оператор Class](/dotnet/visual-basic/language-reference/statements/class-statement) вместо оператора `Module`.  
  
## См. также  
 [Оператор Module](/dotnet/visual-basic/language-reference/statements/module-statement)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Практическое руководство. Определение класса, реализующего одинаковую функциональность для различных типов данных](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)