---
title: "Оператор логического И (&amp;&amp;) (JavaScript) | Microsoft Docs"
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
  - "&&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&& - оператор"
  - "Логический оператор AND"
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Оператор логического И (&amp;&amp;) (JavaScript)
Выполняет логическое умножение двух выражений.  
  
## Синтаксис  
  
```  
  
result = expression1 && expression2   
```  
  
## Параметры  
 `result`  
 Любая переменная.  
  
 `expression1`  
 Любое выражение.  
  
 `expression2`  
 Любое выражение.  
  
## Заметки  
 Если `expression1` равно `false`, `result` равно `expression1`.  В противном случае `result` является `expression2`.  Следовательно, операция возвращает `true`, если оба операнда имеют значение true. В противном случае возвращается `false`.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует следующие правила для преобразования нелогических значений в логические значения.  
  
-   Все объекты считаются `true`.  
  
-   Строки считаются `false`, если они пусты.  
  
-   `null` и `undefined` считаются `false`.  
  
-   Число является `false`, если оно равно нулю.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)