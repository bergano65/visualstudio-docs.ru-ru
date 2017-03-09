---
title: "Ошибка компилятора CS1102 | Microsoft Docs"
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
  - "CS1102"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1102"
ms.assetid: 7de798d4-1b4b-4842-ae43-9bc83e6dc9a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1102
Модификатор параметра "out" не может использоваться с "this"  
  
 Изменение ключевым словом `this` первого параметра статического метода сообщает компилятору, что метод является методом расширения. Никакие другие модификаторы не требуются и не допускаются в первом параметре метода расширения.  
  
### Исправление ошибки  
  
1.  Удалите неразрешенные модификаторы из первого параметра.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1102:  
  
```  
// cs1102.cs // Compile with: /target:library. public static class Extensions { // No type parameters. public static void Test(this out int i) {} // CS1102 //Single type parameter public static void Test<T>(this out T t) {}// CS1102 //Multiple type parameters public static void Test<T,U,V>(this out U u) {}// CS1102 }  
```  
  
## См. также  
 [Методы расширения](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [this](/dotnet/csharp/language-reference/keywords/this)   
 [out](/dotnet/csharp/language-reference/keywords/out)