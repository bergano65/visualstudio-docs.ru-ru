---
title: "Ошибка компилятора CS0526 | Microsoft Docs"
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
  - "CS0526"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0526"
ms.assetid: befc46b4-28ea-40d3-89ac-132b92455772
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0526
Интерфейсы не могут содержать конструкторы.  
  
 Не удается определить конструкторы для [интерфейсов](/dotnet/csharp/language-reference/keywords/interface). Метод считается конструктором, если он имеет то же имя, что и класс, и не имеет тип возврата.  
  
 Следующий пример приводит к возникновению ошибки CS0526:  
  
```  
// CS0526.cs namespace x { public interface clx { public clx()   // CS0526 { } } public class cly { public static void Main() { } } }  
```