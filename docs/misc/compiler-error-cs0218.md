---
title: "Ошибка компилятора CS0218 | Microsoft Docs"
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
  - "CS0218"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0218"
ms.assetid: f675e06a-c55c-44a1-b5db-0df178fd8f79
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0218
Тип \("тип"\) должен содержать объявления оператора true и оператора false  
  
 Если вы задаете оператор для определяемого пользователем типа, а затем пытаетесь использовать его как оператор краткой записи, определяемый пользователем оператор должен иметь заданный оператор true и оператор false. Дополнительные сведения об операторах краткой записи см. в разделах [Оператор &&](/dotnet/csharp/language-reference/operators/conditional-and-operator) и [Оператор &#124;&#124;](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md).  
  
 В следующем примере возникает ошибка CS0218:  
  
```  
// CS0218.cs using System; public class MyClass { // uncomment these operator declarations to resolve this CS0218 /* public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } */ public static implicit operator int(MyClass x) { return 0; } public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f;   // CS0218, requires operators true and false } }  
```  
  
## См. также  
 [Операторы преобразования](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators)