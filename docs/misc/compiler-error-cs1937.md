---
title: "Ошибка компилятора CS1937 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1937"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1937"
ms.assetid: f13e8dc9-8c20-477e-8b74-7192848e08a2
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1937
Имя "имя" не находится в области слева от "equals". Рассмотрите возможность поменять местами выражения с обеих сторон оператора "equals".  
  
 Ключевое слово `equals` — это специальный оператор, который используется в предложении `join` для определения равенства двух выражений. Переменная диапазона для левой части исходной последовательности находится в области с левой стороны от "equals", а переменная диапазона для правой части исходной последовательности — только в области с левой стороны от "equals". Это можно проверить, поэкспериментировав с IntelliSense в следующем примере кода.  
  
### Исправление ошибки  
  
1.  Поменяйте местами две переменные диапазона, как показано в строке комментария в следующем примере:  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1937.  
  
```  
// cs1937.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1937 // Try the following line instead. //join b in sourceB on a equals b select new { a, b }; } }  
```  
  
 Левая сторона обычно называется "внешней", а правая — "внутренней" стороной.  
  
## См. также  
 [Предложение join](/dotnet/csharp/language-reference/keywords/join-clause)