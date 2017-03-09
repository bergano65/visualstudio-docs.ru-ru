---
title: "Ошибка компилятора CS1930 | Microsoft Docs"
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
  - "CS1930"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1930"
ms.assetid: d28d2334-825c-4ffc-b9e9-f5d61f44d672
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1930
Переменная диапазона "имя" уже была объявлена  
  
 Переменная диапазона в выражении запроса находится в области до окончания выражения запроса. Поэтому она должна иметь уникальный идентификатор.  
  
### Исправление ошибки  
  
1.  Присвойте уникальное имя каждой переменной диапазона, включаемой в выражение запроса.  
  
## Пример  
 Приведенный ниже пример приводит к возникновению ошибки CS1930, так как идентификатор `num` используется для переменной диапазона в предложении `from` и для переменной диапазона, представленной предложением `let`.  
  
```  
// cs1930.cs using System.Linq; class Program { static void Main() { int[] nums = { 0, 1, 2, 3, 4, 5 }; var query = from num in nums let num = 3 // CS1930 select num; } }  
```  
  
## См. также  
 [Выражения запросов LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)