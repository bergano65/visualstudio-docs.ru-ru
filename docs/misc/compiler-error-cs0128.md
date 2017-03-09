---
title: "Ошибка компилятора CS0128 | Microsoft Docs"
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
  - "CS0128"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0128"
ms.assetid: 35db9025-2bed-437f-a78a-f2862766bde2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0128
В этой области действия уже определена локальная переменная с именем "переменная"  
  
 Компилятор обнаружил объявления двух локальных переменных с одинаковыми именами. Для получения дополнительной информации см. [Методы](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 Следующий пример приводит к возникновению ошибки CS0128:  
  
```  
// CS0128.cs namespace MyNamespace { public class MyClass { public static void Main() { char i; int i;   // CS0128 } } }  
```