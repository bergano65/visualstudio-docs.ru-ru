---
title: "Ошибка компилятора CS1952 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1952"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1952"
ms.assetid: 8c560bf9-df93-40f5-a3d8-c66b31cde08f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1952
Дерево лямбда\-выражения не может содержать метод с изменяющимся числом аргументов.  
  
 Неподдерживаемое ключевое слово `__arglist` не разрешено в лямбда\-выражениях, которые компилируются в деревья выражений.  
  
### Исправление ошибки  
  
1.  Забудьте, что вы когда\-либо слышали о `__arglist`.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS1952.  
  
```  
// cs1952.cs using System; using System.Linq.Expressions; class Test { public static int M(__arglist) { return 1; } static int Main() { Expression<Func<int, int>> f = x => Test.M(__arglist(x)); // CS1952 return 1; } }  
  
```