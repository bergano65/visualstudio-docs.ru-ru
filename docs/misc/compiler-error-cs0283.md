---
title: "Ошибка компилятора CS0283 | Microsoft Docs"
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
  - "CS0283"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0283"
ms.assetid: f94a5b84-92c5-4602-894d-6f856d57e0e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0283
Тип "тип" не может быть объявлен как константа.  
  
 Тип, указанный в объявлении константы, должны быть типом `byte`, `char`, `short`, `int`, `long`, `float`, `double`, `decimal`, `bool`, `string`, типом перечисления или ссылочным типом, которому присваивается значение null. Каждое константное выражение должно выдавать значение целевого типа или типа, который можно преобразовать в целевой тип путем неявного преобразования.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0283.  
  
```  
// CS0283.cs struct MyTest { } class MyClass { // To resolve the error but retain the "const-ness", // change const to readonly. const MyTest test = new MyTest();   // CS0283 public static int Main() { return 1; } }  
```