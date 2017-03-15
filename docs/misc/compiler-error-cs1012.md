---
title: "Ошибка компилятора CS1012 | Microsoft Docs"
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
  - "CS1012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1012"
ms.assetid: 4acc5fe0-da47-4882-b7d8-557767d7cf03
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1012
Превышение допустимого числа символов в символьной константе.  
  
 Предпринята попытка инициализировать константу [char](/dotnet/csharp/language-reference/keywords/char) с несколькими символами.  
  
 CS1012 может также произойти при выполнении привязки данных. Например, следующая строка кода вызывает эту ошибку:  
  
 `<%# DataBinder.Eval(Container.DataItem, 'doctitle') %>`  
  
 Попробуйте использовать вместо нее следующую строку:  
  
 `<%# DataBinder.Eval(Container.DataItem, "doctitle") %>`  
  
 Следующий пример приводит к возникновению ошибки CS1012:  
  
```  
// CS1012.cs class Sample { static void Main() { char a = 'xx';   // CS1012 char a2 = 'x';   // OK System.Console.WriteLine(a2); } }  
```