---
title: "Оператор присваивания побитового ИЛИ (|=) (JavaScript) | Microsoft Docs"
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
  - "|="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|= - оператор"
  - "операторы присваивания, побитовые [JavaScript]"
  - "побитовые операторы, OR - оператор"
  - "OR - оператор"
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Оператор присваивания побитового ИЛИ (|=) (JavaScript)
Осуществляет логическую операцию побитового ИЛИ для значения переменной и значения выражения, затем присваивает результат переменной.  
  
## Синтаксис  
  
```  
  
result |= expression  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression*  
 Произвольное выражение.  
  
## Заметки  
 Использование данного оператора полностью эквивалентно следующему выражению:  
  
```javascript  
result = result | expression  
```  
  
 Оператор **&#124;\=** рассматривает двоичное представление значений *result* и *expression* и выполняет над ними операцию побитового ИЛИ.  Эта операция дает следующий результат:  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Если любое из выражений содержит 1 в какой\-либо позиции, результат также содержит 1 в этой позиции.  В противном случае результат в этой позиции содержит 0.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор побитового ИЛИ \(&#124;\)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)