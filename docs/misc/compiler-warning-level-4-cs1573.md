---
title: "Предупреждение компилятора (уровень 4) CS1573 | Microsoft Docs"
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
  - "CS1573"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1573"
ms.assetid: 1b68cb1a-9bfd-4343-b9b6-8ce195af5e23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 4) CS1573
Параметр "параметр" не имеет соответствующий тег параметра в XML\-комментарии для "параметра" \(в отличие от остальных параметров\)  
  
 При использовании параметра компилятора [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option) комментарий был указан для некоторых, но не всех параметров в методе. Возможно, вы забыли ввести комментарий для этих параметров.  
  
 Следующий пример приводит к возникновению ошибки CS1573:  
  
```  
// CS1573.cs // compile with: /W:4 public class MyClass { /// <param name='Int1'>Used to indicate status.</param> // enter a comment for Char1? public static void MyMethod(int Int1, char Char1) { } public static void Main () { } }  
```