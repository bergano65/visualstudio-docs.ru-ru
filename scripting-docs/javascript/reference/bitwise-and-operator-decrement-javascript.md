---
title: "Оператор побитового И (&amp;) (JavaScript) | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "операторы присваивания, побитовые [JavaScript]"
  - "оператор &, об операторе &"
  - "AND - оператор"
  - "& - оператор"
  - "побитовые операторы, оператор AND (И)"
  - "оператор &, побитовые операторы"
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Оператор побитового И (&amp;) (JavaScript)
Выполняет побитовую операцию И для двух 32\-битовых выражений.  
  
## Синтаксис  
  
```  
  
result = expression1 & expression2  
```  
  
## Параметры  
 `result`  
 Результат операции.  
  
 `expression1`  
 Произвольное выражение.  
  
 `expression2`  
 Произвольное выражение.  
  
## Заметки  
 `&` выполняет побитовую операцию И для каждого бита двух 32\-битовых выражений.  Если оба бита равны 1, результат равен 1.  В противном случае результат равен 0.  
  
|Бит 1|Бит 2|Результат применения И|  
|-----------|-----------|----------------------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 В следующих примерах показано, как использовать оператор `&`.  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор присваивания побитового И \(&\=\)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)