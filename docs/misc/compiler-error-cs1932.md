---
title: "Ошибка компилятора CS1932 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1932"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1932"
ms.assetid: fc927899-2d35-4d47-9ae9-8fc99295bb66
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1932
Невозможно назначить "выражение" переменной диапазона.  
  
 Компилятор должен иметь возможность вывести тип переменной диапазона, представленной в предложении `from` или `let`. Он не может иметь значение null, поскольку значение null не является типом и не может быть назначено с помощью выражения небезопасного типа.  
  
### Исправление ошибки  
  
-   Удалите назначение, которое является недопустимым.  
  
-   Выполните явное приведение выражения к разрешенному типу.  
  
## Пример  
 Следующий код вызывает ошибку CS1932, поскольку невозможно вывести тип переменной диапазона. Чтобы исправить ошибку, выполните приведение значения к нужному типу, как показано в следующем примере.  
  
```  
// CS1932.cs using System.Linq; class Test { static void Main() { var x = from i in Enumerable.Range(1, 100) let k = null // CS1932 // Try the following line instead. let k = (string) null select i; } }  
```  
  
## См. также  
 [Выражения запросов LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)