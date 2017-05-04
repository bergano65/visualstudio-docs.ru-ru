---
title: "Оператор присваивания побитового исключающего ИЛИ (^=) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "^="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "^= - оператор"
  - "^= - оператор, сведения об операторе ^="
  - "операторы присваивания, побитовые [JavaScript]"
  - "побитовые операторы, XOR - оператор"
  - "XOR - оператор"
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Оператор присваивания побитового исключающего ИЛИ (^=) (JavaScript)
Выполняет логическую операцию побитового исключающего ИЛИ для значения переменной и значения выражения, затем присваивает результат переменной.  
  
## Синтаксис  
  
```  
  
result ^= expression  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression*  
 Произвольное выражение.  
  
## Заметки  
 Использование оператора **^\=** полностью эквивалентно следующему выражению:  
  
```javascript  
result = result ^ expression  
```  
  
 После этого оператор **^\=** рассматривает двоичное представление значений двух выражений и выполняет над ними операцию побитового исключающего ИЛИ.  Результат операции выглядит следующим образом:  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Если одно, и только одно, выражение содержит 1 в какой\-либо позиции, результат содержит 1 в этой позиции.  В противном случае результат в этой позиции содержит 0.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор побитового исключающего ИЛИ \(^\)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)