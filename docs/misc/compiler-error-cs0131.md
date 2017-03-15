---
title: "Ошибка компилятора CS0131 | Microsoft Docs"
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
  - "CS0131"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0131"
ms.assetid: 822852cc-a426-4b7d-b2ff-0026a0c0a0e7
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0131
Левая часть выражения присваивания должна быть переменной, свойством или индексатором  
  
 В операторах присваивания значение правой части выражения присваивается левой части выражения. Левая часть выражения должна быть переменной, свойством или индексатором.  
  
 Чтобы устранить эту ошибку, убедитесь в том, что все операторы находятся в правой части выражения, а левая часть является переменной, свойством или индексатором. Для получения дополнительной информации см. [Инструкции, выражения и операторы](/dotnet/csharp/programming-guide/statements-expressions-operators/index).  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0131:  
  
```  
// CS0131.cs public class MyClass { public int i = 0; public void MyMethod() { i++ = 1;   // CS0131 // try the following line instead // i = 1; } public static void Main() { } }  
```  
  
## Пример  
 Эта ошибка может также возникать при попытке выполнить арифметические операции в левой части оператора присваивания, как показано в приведенном ниже примере.  
  
```  
// CS0131b.cs public class C { public static int Main() { int a = 1, b = 2, c = 3; if (a + b = c) // CS0131 // try this instead // if (a + b == c) return 0; return 1; } }  
```