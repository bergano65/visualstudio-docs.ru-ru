---
title: "Ошибка компилятора CS1953 | Microsoft Docs"
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
  - "CS1953"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1953"
ms.assetid: b8af5eed-0f3b-4258-b4e2-f5d184288239
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1953
Дерево лямбда\-выражения не может содержать группу методов.  
  
 Для вызова метода требуется оператор `()`. Имя метода без этого оператора ссылается на группу методов, которая представляет собой набор всех перегруженных методов с этим именем.  
  
### Исправление ошибки  
  
1.  Если предполагается вызывать этот метод, добавьте оператор `()`.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1953:  
  
```  
// cs1953.cs using System; using System.Linq.Expressions; class CS1953 { public static void Main() { double num = 10; Expression<Func<bool>> testExpr = () => num.GetType is int; // CS1953 } }  
```