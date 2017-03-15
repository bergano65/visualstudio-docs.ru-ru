---
title: "Ошибка компилятора CS0687 | Microsoft Docs"
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
  - "CS0687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0687"
ms.assetid: b51c5e7c-f4de-4aa4-97b1-ebe220cd19b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0687
Квалификатор псевдонима пространства имен "::" всегда разрешается в тип или пространство имен, что в данном случае недопустимо. Рассмотрите возможность использования "." вместо "::".  
  
 Эта ошибка возникает, если нечто, интерпретируемое средством синтаксического анализа как тип, используется в неподходящем месте. Имя типа или пространства имен допустимо только в выражении доступа к членам, с использованием оператора доступа к членам \(**.**\). Это может произойти при использовании оператора глобальной области \(::\) в другом контексте.  
  
## Пример  
 В следующем примере происходит ошибка CS0687.  
  
```  
// CS0687.cs using M = Test; using System; public class Test { public static int x = 77; public static void Main() { Console.WriteLine(M::x); // CS0687 // To resolve use the following line instead: // Console.WriteLine(M.x); } }  
```