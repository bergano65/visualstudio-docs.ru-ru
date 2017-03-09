---
title: "Ошибка компилятора CS0111 | Microsoft Docs"
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
  - "CS0111"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0111"
ms.assetid: 87afb689-f27b-451d-84eb-d6bdf17aea41
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0111
Тип "класс" уже определяет член с именем "член" с теми же типами параметров  
  
 Ошибка CS0111 возникает, если класс содержит два объявления членов с одинаковыми именами и типами параметров. Для получения дополнительной информации см. [Методы](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0111.  
  
```  
// CS0111.cs class A { void Test() { } public static void Test(){}   // CS0111 public static void Main() {} }  
```