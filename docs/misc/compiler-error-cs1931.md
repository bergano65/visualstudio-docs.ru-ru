---
title: "Ошибка компилятора CS1931 | Microsoft Docs"
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
  - "CS1931"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1931"
ms.assetid: c0071c3d-ae11-4073-87df-508150daef68
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1931
Переменная диапазона "переменная" конфликтует с предыдущим объявлением переменной "переменная".  
  
 Объявление переменной диапазона, как и любое другие объявление, должно иметь идентификатор, который является уникальным в области объявления переменной.  
  
### Исправление ошибки  
  
1.  Задайте уникальное имя для переменной диапазона.  
  
## Пример  
 Следующий код создает ошибку CS1931, так как идентификатор `x` используется и как локальная переменная в `Main`, и как переменная диапазона в выражении запроса:  
  
```  
// cs1931.cs class Test { static void Main() { int x = 1; var y = from x in Enumerable.Range(1, 100) // CS1931 select x; } }  
```  
  
## См. также  
 [Выражения запросов LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)