---
title: "IsNot требуются операнды, имеющие ссылочные типы, а этот операнд имеет тип значения &quot;&lt;имя_типа&gt;&quot;. | Microsoft Docs"
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
  - "bc31419"
  - "vbc31419"
helpviewer_keywords: 
  - "BC31419"
ms.assetid: c44d2936-8c07-443a-b320-ac2bfbc1e9ec
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# IsNot требуются операнды, имеющие ссылочные типы, а этот операнд имеет тип значения &quot;&lt;имя_типа&gt;&quot;.
Выражение использует [Оператор IsNot](/dotnet/visual-basic/language-reference/operators/isnot-operator) с по крайней мере одним операндом типа значения.  
  
 Оператор `IsNot` определяет, ссылаются ли две ссылки на разные объекты. Он сравнивает значения указателей ссылочных типов и не имеет смысла для типов значений.  
  
 **Идентификатор ошибки:** BC31419  
  
### Исправление ошибки  
  
-   Если нужно сравнить значения двух типов значений, используйте оператор сравнения `=` или `<>`.  
  
-   Если вы планируете сравнивать указатели двух ссылочных типов, убедитесь, что для обоих операндов используются ссылки на объекты. Вы можете использовать ссылочные переменные или элементы, такие как ключевое слово [Me](http://msdn.microsoft.com/ru-ru/a65973c7-cf06-4547-9b25-9fba885525c2), которые ведут себя как ссылочные переменные.  
  
## См. также  
 [Операторы сравнения в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Практическое руководство. Проверка совпадения двух объектов](../Topic/How%20to:%20Test%20Whether%20Two%20Objects%20Are%20the%20Same%20\(Visual%20Basic\).md)