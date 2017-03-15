---
title: "Ошибка компилятора CS0017 | Microsoft Docs"
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
  - "CS0017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0017"
ms.assetid: 5e2a3eb3-6f6e-485d-8293-ceabea4d6905
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0017
Программа "имя выходного файла" имеет несколько заданных точек входа. Выполните компиляцию с параметром \/main, чтобы указать тип, который содержит точку входа.  
  
 Программа может иметь только один метод [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments).  
  
 Чтобы устранить эту ошибку, можно либо удалить в коде все методы Main, кроме одного, или с помощью параметра компилятора [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) указать, какой метод Main вы хотите использовать.  
  
 Следующий пример приводит к возникновению ошибки CS0017:  
  
```  
// CS0017.cs // compile with: /target:exe public class clx { static public void Main() { } } public class cly { public static void Main()   // CS0017, delete one Main or use /main { } }  
```