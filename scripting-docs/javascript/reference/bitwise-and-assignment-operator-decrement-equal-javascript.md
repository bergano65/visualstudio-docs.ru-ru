---
title: "Оператор присваивания побитового И (&amp;=) (JavaScript) | Microsoft Docs"
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
  - "&="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&= - оператор"
  - "операторы присваивания, побитовые [JavaScript]"
  - "AND - оператор"
  - "побитовые операторы, оператор И"
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Оператор присваивания побитового И (&amp;=) (JavaScript)
Устанавливает результат операции побитового И для значения переменной и значения выражения.  Переменная и выражение обрабатываются как 32\-разрядные целые числа.  
  
## Синтаксис  
  
```  
  
result &= expression  
```  
  
## Параметры  
 `result`  
 Любая переменная.  
  
 `expression`  
 Произвольное выражение.  
  
## Заметки  
 Использование данного оператора эквивалентно следующему выражению:  
  
```javascript  
result = result & expression  
```  
  
 Оператор [Оператор побитового И \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) рассматривает двоичное представление значений `result` и `expression` и выполняет над ними операцию побитового И.  Выходные данные этой операции ведут себя следующим образом:  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
  
```  
  
 Если оба выражения содержат 1 в какой\-либо позиции, результат также содержит 1 в этой позиции.  В противном случае результат в этой позиции содержит 0.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор побитового И \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)