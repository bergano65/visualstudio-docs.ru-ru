---
title: "Оператор побитового исключающего ИЛИ (^) (JavaScript) | Microsoft Docs"
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
  - "^"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "побитовые операторы, XOR - оператор"
  - "XOR - оператор"
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Оператор побитового исключающего ИЛИ (^) (JavaScript)
Выполняет побитовую операцию исключающего ИЛИ для двух выражений.  
  
## Синтаксис  
  
```  
  
result = expression1 ^ expression2  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression1*  
 Произвольное выражение.  
  
 *expression2*  
 Произвольное выражение.  
  
## Заметки  
 Оператор **^** рассматривает двоичное представление значений двух выражений и выполняет над ними операцию побитового исключающего ИЛИ.  Результат операции выглядит следующим образом:  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 Если одно, и только одно, выражение содержит 1 в какой\-либо позиции, результат содержит 1 в этой позиции.  В противном случае результат в этой позиции содержит 0.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор присваивания побитового исключающего ИЛИ \(^\=\)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)