---
title: "Оператор логического НЕ (!) (JavaScript) | Microsoft Docs"
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
  - "!"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "! оператор"
  - "! оператор, сведения об операторе !"
  - "оператор логического НЕ"
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Оператор логического НЕ (!) (JavaScript)
Выполняет логическое отрицание выражения.  
  
## Синтаксис  
  
```  
  
result = !expression  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression*  
 Произвольное выражение.  
  
## Заметки  
 В следующей таблице показано, как определяется результат *result*.  
  
|Если `expression` имеет значение|Значение `result`|  
|--------------------------------------|-----------------------|  
|True|False|  
|False|True|  
  
 Все унарные операторы, такие как **\!**, вычисляют выражения следующим образом.  
  
-   Если оператор применяется к неопределенному значению или выражению `null`, возникает ошибка времени выполнения.  
  
-   Объекты преобразуются в строки.  
  
-   Строки преобразуются в числа, если это возможно.  Если это невозможно, возникает ошибка времени выполнения.  
  
-   Логические значения интерпретируются как числа \(0 для false, 1 для true\).  
  
 Оператор применяется к результирующему числу.  
  
 Если в случае оператора **\!** *выражение* не равно нулю, *результат* равен нулю.  Если *выражение* равно нулю, *результат* равен 1.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор побитового НЕ \(~\)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)