---
title: "Ошибка компилятора CS0119 | Microsoft Docs"
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
  - "CS0119"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0119"
ms.assetid: 048924f1-378f-4021-bd20-299d3218f810
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0119
"конструкция1\_имя" является "конструкция1", которая недопустима в данном контексте.  
  
 Компилятор обнаружил одну из следующих непредвиденных конструкций:  
  
-   конструктор класса не является допустимым тестовым выражением в условном операторе;  
  
-   для ссылки на элемент массива использовалось имя класса вместо имени экземпляра;  
  
-   идентификатор метода использовался так, как если бы он был структурой или классом.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS0119.  
  
```  
// CS0119.cs using System; public class MyClass { public static void Test() {} public static void Main() { Console.WriteLine(Test.x);   // CS0119 } }  
```