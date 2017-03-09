---
title: "Ошибка компилятора CS0715 | Microsoft Docs"
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
  - "CS0715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0715"
ms.assetid: e3cd1e46-ccfa-4678-a2ed-69245f3558ba
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0715
"статический\_класс": статические классы не могут содержать определяемые пользователем операторы  
  
 Определяемые пользователем операторы работают с экземплярами классов. Экземпляры статических классов создать нельзя, поэтому невозможно создать экземпляры для работы операторов. Таким образом, определяемые пользователем операторы для статических классов не разрешены.  
  
 Следующий пример приводит к возникновению ошибки CS0715:  
  
```  
// CS0715.cs public static class C { public static C operator+(C c)  // CS0715 { } public static void Main() { } }  
```