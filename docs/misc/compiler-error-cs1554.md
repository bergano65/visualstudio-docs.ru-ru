---
title: "Ошибка компилятора CS1554 | Microsoft Docs"
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
  - "CS1554"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1554"
ms.assetid: 81e8d4ac-cdbf-4b75-8932-0bc271a8405c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1554
Объявление недействительно; используйте "\<тип\> оператор \<оператор\> \(..."  
  
 Тип возвращаемых данных для пользовательского [оператора](/dotnet/csharp/language-reference/keywords/operator) должен находиться перед ключевым словом operator.  
  
 Следующий пример приводит к возникновению ошибки CS1554:  
  
```  
// CS1554.cs class MyClass { public static operator ++ MyClass (MyClass f)    // CS1554 // try the following line instead // public static MyClass operator ++ (MyClass f) { return new MyClass (); } public static void Main() { } }  
```