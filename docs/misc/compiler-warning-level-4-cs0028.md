---
title: "Предупреждение компилятора (уровень 4) CS0028 | Microsoft Docs"
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
  - "CS0028"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0028"
ms.assetid: 47df919f-01fa-45ae-a4b7-912445e679e2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 4) CS0028
"объявление функции" имеет неправильную сигнатуру и не может быть точкой входа  
  
 Объявление метода для `Main` было неправильным: метод был объявлен с недопустимой сигнатурой.`Main` должен быть объявлен как статический и возвращать тип [int](/dotnet/csharp/language-reference/keywords/int) или [void](/dotnet/csharp/language-reference/keywords/void). Дополнительные сведения см. в разделе [Main\(\) и аргументы командной строки](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments).  
  
 В следующем примере происходит ошибка CS0028:  
  
```  
// CS0028.cs // compile with: /W:4 /warnaserror public class a { public static double Main(int i)   // CS0028 // Try the following line instead: // public static void Main() { } }  
```