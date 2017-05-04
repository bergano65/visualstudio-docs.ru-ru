---
title: "Оператор побитового ИЛИ (|) (JavaScript) | Microsoft Docs"
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
  - "|"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "| - оператор"
  - "побитовые операторы, OR - оператор"
  - "OR - оператор"
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Оператор побитового ИЛИ (|) (JavaScript)
Выполняет операцию побитового ИЛИ для двух выражений.  
  
## Синтаксис  
  
```  
  
result = expression1 | expression2  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression1*  
 Произвольное выражение.  
  
 *expression2*  
 Произвольное выражение.  
  
## Заметки  
 Оператор          **&#124;** рассматривает двоичное представление значений двух выражений и выполняет над ними операцию побитового ИЛИ.  Результат операции выглядит следующим образом:  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 Если какое\-либо из выражений содержит в цифровой позиции 1, результат также содержит 1 в этой позиции.  В противном случае результат в этой позиции содержит 0.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор присваивания побитового ИЛИ \(&#124;\=\)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)