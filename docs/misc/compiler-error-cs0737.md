---
title: "Ошибка компилятора CS0737 | Microsoft Docs"
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
  - "CS0737"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0737"
ms.assetid: d2247770-5546-46f2-a01d-8e2ebfcbb859
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0737
"имя типа" не реализует член интерфейса "имя члена". "имя\_метода" не может реализовать член интерфейса, потому что он не является открытым.  
  
 Метод, который реализует член интерфейса, должен быть открытым. Все члены интерфейса являются `public`.  
  
### Исправление ошибки  
  
1.  Добавьте модификатор доступа [public](/dotnet/csharp/language-reference/keywords/public) в метод.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0737:  
  
```  
// cs0737.cs interface ITest { // Default access of private with no modifier. int Return42(); // Try the following line instead. // public int Return42(); } struct Struct1 : ITest // CS0737 { int Return42() { return (42); } } public class Test { public static int Main(string[] args) { Struct1 s1 = new Struct1(); return (1); } }  
```  
  
## См. также  
 [Интерфейсы](/dotnet/csharp/programming-guide/interfaces/index)