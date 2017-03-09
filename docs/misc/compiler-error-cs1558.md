---
title: "Ошибка компилятора CS1558 | Microsoft Docs"
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
  - "CS1558"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1558"
ms.assetid: ee603d66-007e-4782-9285-7ff031975f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1558
Класс "класс" не имеет подходящего статического метода Main  
  
 Параметр компилятора [\/Main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) задает класс, в котором следует искать метод **Main**. Однако метод [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) не был определен правильно.  
  
 В следующем примере возникает ошибка CS1558 из\-за недопустимого типа возврата.  
  
```  
// CS1558.cs // compile with: /main:MyNamespace.MyClass namespace MyNamespace { public class MyClass { public static float Main() { return 0.0; // CS1558 because the return type is a float. } } }  
```